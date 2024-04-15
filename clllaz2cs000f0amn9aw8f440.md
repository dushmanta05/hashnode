---
title: ""First-Class Function" and "Higher Order Function""
datePublished: Mon Aug 21 2023 20:01:36 GMT+0000 (Coordinated Universal Time)
cuid: clllaz2cs000f0amn9aw8f440
slug: first-class-function-and-higher-order-function
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692647844231/6f3efe3b-3277-42b0-b69f-d5cacce7208e.jpeg
tags: javascript, higher-order-functions, first-class-functions

---

While learning JavaScript functions, you must have come across these two words: "first-class function" and "higher-order function", Let's understand these with examples. The only prerequisite you need is knowledge about functions.

### First-Class Function

In a programming language, a function can be considered a **first-class function** if it can be:

* Assigned to variables
    
* Passed as an argument to other functions
    
* Returned from another function
    
* Stored in arrays or objects
    

So basically, we can say first-class functions are treated similarly to data types in JavaScript.

Let's understand how we can **assign a variable** to a function through an example:

```javascript
// A function to add 2 numbers
function add(num1, num2) {
    return num1 + num2;
}
console.log(add(3, 4)); // Output: 7

/* Like we assign values to variables,
we can also assign functions as values 
to variables */

var addFunc = function(num1, num2) {
    return num1 + num2;
};

/* The above variable "addFunc" will also 
return the same result as the "add" function */

console.log(addFunc(3, 4)); // Output: 7
```

As you can see in the above code snippet, due to first-class functions, we're able to assign a variable to the function.

Now let's understand passing a **function as an argument**.

Suppose we have a project where basic arithmetic operations such as addition, subtraction, multiplication, and division are required. With our basic understanding of functions, we can accomplish this using the following code:

```javascript
// Addition function
function add(num1, num2){
    return num1 + num2;
}

// Subtract function
function sub(num1, num2){
    return num1 - num2;
}

// Multiplication function
function multi(num1, num2){
    return num1 * num2;
}

// Division function
function div(num1, num2){
    return num1 / num2;
}

console.log(add(9, 3)); // Output: 12
console.log(sub(9, 3)); // Output: 6
console.log(multi(9, 3)); // Output: 27
console.log(div(9, 3)); // Output: 3
```

Now, let's imagine a scenario where we find ourselves needing to perform these arithmetic operations repeatedly. With the current approach, we'd have to call each function—addition, subtraction, multiplication, and division—multiple times, resulting in a considerable amount of repetitive code.

However, as developers, we strive to make our code efficient and avoid unnecessary repetition. Wouldn't it be great if there were a way to consolidate these operations into a single function, where we only need to specify the desired operation and get the result? This is where passing a function as an argument comes into the picture.

In this context, we can create a dedicated function for calculation. This function would accept an arithmetic operation function as an argument and then produce the appropriate results. To better grasp this concept, let's modify the code we discussed earlier.

```javascript
// create calculation function
function calculation(num1, num2, operator)
    /* here calculation function is taking operator 
    function as an argument */
    {
    return operator(num1, num2);
    }

// Let's pass the function as an argument now and observe the results
console.log(calculation(9, 3, add));   // Output: 12
console.log(calculation(9, 3, sub));   // Output: 6
console.log(calculation(9, 3, multi)); // Output: 27
console.log(calculation(9, 3, div));   // Output: 3
```

As you can observe in the code snippet above, we're able to pass a function as an argument and obtain the desired output. While this example may be modest, in more substantial programs, this capability proves to be incredibly useful.

### Higher-Order Function

Now, what if I were to tell you that you've already encountered a higher-order function in the example above? Yes, you heard that right. The `calculation` function we used is a **higher-order function.**

Definition: A function is considered a higher-order function if it either accepts other functions as arguments, returns another function or could be both.

We've already witnessed an example of how a **higher-order function** can accept another function as an argument. Now, let's explore the other side of the coin: returning a function from a higher-order function. To do this, we can modify the same example we discussed earlier.

Now, let's go a step further and place the arithmetic operator logic right inside the `calculation` function. We'll see how a **higher-order function** can return another function. Check out the modified code below.

```javascript
// Create the calculation function
function calculation(operator) {
    if (operator === "add") {
        return function(num1, num2) {
            return num1 + num2;
        };
    } else if (operator === "sub") {
        return function(num1, num2) {
            return num1 - num2;
        };
    } else if (operator === "multi") {
        return function(num1, num2) {
            return num1 * num2;
        };
    } else if (operator === "div") {
        return function(num1, num2) {
            return num1 / num2;
        };
    } else {
        return null;
    }
}

// Get operation functions
const addOperation = calculation("add");
const subOperation = calculation("sub");
const multiOperation = calculation("multi");
const divOperation = calculation("div");

// Perform calculations using the returned functions
console.log(addOperation(9, 3));   // Output: 12
console.log(subOperation(9, 3));   // Output: 6
console.log(multiOperation(9, 3)); // Output: 27
console.log(divOperation(9, 3));   // Output: 3
```

As you can see above, we got the returned function, and we also assigned a variable to it as we discussed in the first point, and we got our desired results.

I hope that with the concepts we've explored, you now have a solid grasp of first-class functions and higher-order functions.

Furthermore, during my learning of this concept, one question arose in my mind: Can we have more than one higher-order function in a single nested function? The answer is yes. If the function we're passing as an argument also takes another function as an argument, then it, too, can be referred to as a higher-order function.

Let's have an example

```javascript
// Addition function
function addition(num1, num2) {
    return num1 + num2;
}

// Higher-order function
function higherOrderFunc(operator) {
    // Nested higher-order function
    function nestedHigherOrderFunc(callback, num1, num2) {
        return callback(num1, num2);
    }
    // returning the nestedHigherOrderFunc
    return nestedHigherOrder(operator, 5, 3);
}

// Calling the higher-order function with the addition function
const result = higherOrderFunc(addition);
console.log(result); // Output: 8 (5 + 3)
```

Above, we have a higher-order function where we pass an operator function as an argument. Inside this higher-order function, there's a nested higher-order function that also takes the operator as an argument. This demonstrates the possibility of having multiple higher-order functions within a single nested function.

Moving on to the final aspect of first-class functions: the ability to **store functions in arrays and objects**.

Storing functions in arrays and objects can be beneficial. For instance, let's consider an example where we store various arithmetic operation functions in an array and access them as needed.

```javascript
// Addition function
function addition(num1, num2) {
    return num1 + num2;
}

// Subtraction function
function subtraction(num1, num2) {
    return num1 - num2;
}

// Multiplication function
function multiplication(num1, num2) {
    return num1 * num2;
}

// Division function
function division(num1, num2) {
    return num1 / num2;
}

// Array to store arithmetic operation functions
const operationFunctions = [addition, subtraction, multiplication, division];

// Accessing and using functions from the array
const result1 = operationFunctions[0](5, 3); // Addition
const result2 = operationFunctions[1](8, 2); // Subtraction

console.log(result1); // Output: 8 (5 + 3)
console.log(result2); // Output: 6 (8 - 2)
```

Likewise, you can store functions as parts of objects to create methods. For instance, let's build an object named `calculation` with methods for addition, subtraction, multiplication, and division. This allows us to perform calculations directly on the object.

```javascript
// Object with calculation methods
const calculation = {
    add: function(num1, num2) {
        return num1 + num2;
    },
    sub: function(num1, num2) {
        return num1 - num2;
    },
    multi: function(num1, num2) {
        return num1 * num2;
    },
    div: function(num1, num2) {
        return num1 / num2;
    }
};

// Using methods from the calculation object
const sum = calculation.add(5, 3);        
const difference = calculation.sub(8, 2); 

console.log(sum); // Output: 8
console.log(difference); // Output: 6
```

I hope that you have a clear understanding of **first-class functions** and **higher-order functions**. Feel free to share your thoughts and any suggestions for improvement. Thank you!