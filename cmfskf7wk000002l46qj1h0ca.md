---
title: "Transform PostgreSQL into a Vector Database with pgvector"
seoTitle: "Convert PostgreSQL to Vector DB with pgvector"
seoDescription: "Learn how to use PostgreSQL as a vector database with pgvector for storing and querying embeddings in RAG applications"
datePublished: Sat Sep 20 2025 17:51:40 GMT+0000 (Coordinated Universal Time)
cuid: cmfskf7wk000002l46qj1h0ca
slug: transform-postgresql-into-a-vector-database-with-pgvector
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1758390601474/dcd829ab-2b65-41bb-a6f4-67f96ab28d7a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1758390653215/9cfc8046-8ee1-4fbb-bebc-0592496805bb.png
tags: vector-database, pgvector

---

Building a RAG application is currently a popular topic, and one key requirement is a vector store or database to store and query embeddings. While there are specialized vector databases available, we can also use the OG `PostgreSQL` as a vector database thanks to the [pgvector](https://github.com/pgvector/pgvector) extension.

In this article, we'll explore how to integrate with an existing PostgreSQL database. The [official repository](https://github.com/pgvector/pgvector) also explains how to install it, so you can check there for more details.

If you're starting from scratch, there's a [Docker image](https://hub.docker.com/r/pgvector/pgvector) available with built-in vector support, officially maintained by the `pgvector` community. If you already have a database, it's better to integrate with it since it already contains data.

## Prerequisite:

Before starting, ensure you have a container running with PostgreSQL. If it's installed locally, make sure it's running on your system.

## Installation:

### Find PostgreSQL Container

Since we're using PostgreSQL in a container, let's locate the container with the following command:

```bash
docker ps
```

This will list all the containers running on our system. You need to check the `Names` column to find the name of the Postgres container. Alternatively, you can list only the containers running from the Postgres image with the following command:

```bash
docker ps --filter "ancestor=postgres"
```

Here are my results for the above command:

```bash
CONTAINER ID   IMAGE             COMMAND                  CREATED       STATUS       PORTS                                       NAMES
36622542432f   postgres:latest   "docker-entrypoint.s…"   3 weeks ago   Up 4 hours   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   postgres_container
```

Now, as you can see, my container name is `postgres_container`.

Next, let's open the container using a terminal with the following command:

```bash
docker exec -it <container-name> bash
# docker exec -it postgres_container bash
```

### Installing `pgvector`

Now, the Docker image is based on an Ubuntu (Debian-based Linux distribution) image. Since we're inside the Docker image, we can run `apt` commands. We need to install some packages to ensure essential tools are available to build the extension, as well as all necessary packages for Postgres to use the `pgvector` extension.

You can install the necessary packages with the following command:

```bash
apt-get update
apt-get install -y build-essential git postgresql-server-dev-all
```

Now that these packages are installed, let's proceed with installing the `pgvector` extension.

First, let's copy the source from the official repository (preferably in the root directory).

```bash
git clone https://github.com/pgvector/pgvector.git
```

Next, install the extension from this source with the following command:

```bash
cd pgvector
make
make install
```

After successfully installing, exit and restart the container using the following command:

```bash
docker restart <container-name>
# docker restart postgres_container
```

Now that the `pgvector` extension is successfully added to the container, the next step is to enable it for the database which we will integrate with `pgvector`.

### Enable `pgvector`

First, let's connect to the PostgreSQL database instance from our terminal using the following command:

```bash
docker exec -it <container-name> psql -h localhost -U <db-user> -d <db-name>

# docker exec -it postgres_container psql -h localhost -U dushmanta -d klansity
```

After successfully connecting, run the following command to create the extension in the database:

```bash
CREATE EXTENSION vector;
```

This command will create the vector extension in the database we are logged into.

Next, let's double-check if it appears in the extensions using the following command:

```bash
\dx
```

If the vector extension is successfully created, you'll see it in the results. In my case, this is how it appears:

```bash
List of installed extensions
  Name   | Version |   Schema   |                     Description                      
---------+---------+------------+------------------------------------------------------
 plpgsql | 1.0     | pg_catalog | PL/pgSQL procedural language
 vector  | 0.8.0   | public     | vector data type and ivfflat and hnsw access methods
(2 rows)
```

After successfully installing, let's check if it works.

## Testing

Here, we'll create a table with vector fields. Then, we'll store some vectors, fetch them, and see if it works.

### Create Table

We'll create a table named `pgvector` with a field called `embedding`, which is a vector field with a dimension of 3, using the following command.

```pgsql
CREATE TABLE pgvector (
    id SERIAL PRIMARY KEY,
    content TEXT,
    embedding VECTOR(3)
);
```

If you want to learn more about vector dimensions, I suggest checking out these [Cloudflare docs](https://developers.cloudflare.com/vectorize/best-practices/create-indexes/#dimensions).

> Note: Set the dimensions based on the model you’re going to use to generate the vector embedding.

If you have `pgAdmin`, `Adminer`, or `phpMyAdmin` running, check if the database is created. You can also verify this in the terminal with the following command.

```bash
\d pgvector
```

My results looked like this:

```pgsql
                               Table "public.pgvector"
  Column   |   Type    | Collation | Nullable |               Default                
-----------+-----------+-----------+----------+--------------------------------------
 id        | integer   |           | not null | nextval('pgvector_id_seq'::regclass)
 content   | text      |           |          | 
 embedding | vector(3) |           |          | 
Indexes:
    "pgvector_pkey" PRIMARY KEY, btree (id)
```

And in `Adminer`, it looks something like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1758346855418/88b1c97a-04f7-48e4-a0ba-07598930a72e.png align="left")

### Insert Vector Embedding

Now let’s insert a vector embedding into the embedding field using the following command:

```pgsql
INSERT INTO pgvector (content, embedding) VALUES
('first doc', '[1,2,3]'),
('second doc', '[4,5,6]');
```

This will create two records. Let's check the records.

> Note: In real use cases these embedding will be generated by models and the vector numerical values will be very different.

```pgsql
SELECT * FROM pgvector;
```

Here are the results:

```pgsql
 id |  content   | embedding 
----+------------+-----------
  1 | first doc  | [1,2,3]
  2 | second doc | [4,5,6]
(2 rows)
```

### Vector Search

Now that we've added two records with vector data, let's perform a vector search using the vector `[1,2,2]` to find which data is closest to it with the following command:

```pgsql
SELECT id, content, embedding
FROM pgvector
ORDER BY embedding <-> '[1,2,2]' -- THe <-> symbol is used for vector search
LIMIT 1;
```

The result will be the following:

```pgsql
 id |  content  | embedding 
----+-----------+-----------
  1 | first doc | [1,2,3]
(1 row)
```

As you can see, it fetched the `[1,2,3]` value as its nearest.

### Delete Table

Since we created this table for testing purposes, let’s delete it with the following command.

```pgsql
DROP TABLE pgvector;
```

Now we have successfully installed the `pgvector` extension and can use our `PostgreSQL` database as a vector database for GenAI applications.

---

This article is intended as a personal note, but if you're looking to integrate pgvector, I hope you find it helpful. If you notice any mistakes or have any issues, please feel free to contact me. Thank you.