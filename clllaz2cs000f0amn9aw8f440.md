---
title: "Exploring the Concepts of First-Class and Higher-Order Functions"
seoTitle: "First-Class and Higher-Order Functions Explained"
seoDescription: "Understanding first-class and higher-order functions in JavaScript with examples to enhance your programming efficiency and code organization"
datePublished: Mon Aug 21 2023 20:01:36 GMT+0000 (Coordinated Universal Time)
cuid: clllaz2cs000f0amn9aw8f440
slug: first-class-function-and-higher-order-function
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692647844231/6f3efe3b-3277-42b0-b69f-d5cacce7208e.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1721589115055/20539407-b0a2-4578-9ebd-1afae92fa0c4.jpeg
tags: javascript, higher-order-functions, first-class-functions

---

While learning JavaScript functions, you may have encountered the terms "first-class function" and "higher-order function." Let's understand these with examples. The only prerequisite is a basic understanding of functions.

### First-Class Function

In a programming language, a function is considered a **first-class function** if it can be:

* Assigned to variables
    
* Passed as an argument to other functions
    
* Returned from another function
    
* Stored in arrays or objects
    

In simple terms, first-class functions are treated like data types in JavaScript.

Let's understand how we can **assign a function to a variable** through an example:

```javascript
// A function to add 2 numbers
function add(num1, num2) {
   return num1 + num2;
}
console.log(add(3, 4)); // Output: 7

/* Like we assign values to variables,
we can also assign functions as values 
to variables */

var addFunc = function (num1, num2) {
   return num1 + num2;
};

/* The above variable "addFunc" will also 
return the same result as the "add" function */

console.log(addFunc(3, 4)); // Output: 7
```

As you can see in the code snippet above, first-class functions allow us to assign a function to a variable.

Now let's understand passing a **function as an argument**.

Suppose we have a project that requires basic arithmetic operations like addition, subtraction, multiplication, and division. With our basic understanding of functions, we can achieve this using the following code:

```javascript
// Addition function
function add(num1, num2) {
   return num1 + num2;
}

// Subtract function
function sub(num1, num2) {
   return num1 - num2;
}

// Multiplication function
function multi(num1, num2) {
   return num1 * num2;
}

// Division function
function div(num1, num2) {
   return num1 / num2;
}

console.log(add(9, 3)); // Output: 12
console.log(sub(9, 3)); // Output: 6
console.log(multi(9, 3)); // Output: 27
console.log(div(9, 3)); // Output: 3
```

Now, let's imagine a situation where we need to perform these arithmetic operations repeatedly. With the current approach, we'd have to call each function—addition, subtraction, multiplication, and division—multiple times, leading to a lot of repetitive code.

As developers, we aim to make our code efficient and avoid unnecessary repetition. Wouldn't it be great if we could combine these operations into a single function, where we only need to specify the desired operation and get the result? This is where passing a function as an argument comes into play.

We can create a dedicated calculation function that accepts an arithmetic operation function as an argument and then produces the appropriate results. To understand this concept better, let's modify the code we discussed earlier.

```javascript
// create calculation function
function calculation(num1, num2, operator)
/* here calculation function is taking operator 
function as an argument */
{
   return operator(num1, num2);
}

// Let's pass the function as an argument now and observe the results
console.log(calculation(9, 3, add)); // Output: 12
console.log(calculation(9, 3, sub)); // Output: 6
console.log(calculation(9, 3, multi)); // Output: 27
console.log(calculation(9, 3, div)); // Output: 3
```

As you can see in the code snippet above, we can pass a function as an argument and get the desired output. While this example is simple, in larger programs, this capability is incredibly useful.

### Higher-Order Function

Now, what if I told you that you've already encountered a higher-order function in the example above? Yes, that's right. The `calculation` function we used is a **higher-order function.**

Definition: A function is considered a higher-order function if it either accepts other functions as arguments, returns another function, or does both.

We've already seen how a **higher-order function** can accept another function as an argument. Now, let's explore the other side: returning a function from a higher-order function. To do this, we can modify the example we discussed earlier.

Let's go a step further and place the arithmetic operator logic right inside the `calculation` function. We'll see how a **higher-order function** can return another function. Check out the modified code below.

```javascript
// Create the calculation function
function calculation(operator) {
   if (operator === "add") {
      return function (num1, num2) {
         return num1 + num2;
      };
   } else if (operator === "sub") {
      return function (num1, num2) {
         return num1 - num2;
      };
   } else if (operator === "multi") {
      return function (num1, num2) {
         return num1 * num2;
      };
   } else if (operator === "div") {
      return function (num1, num2) {
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
console.log(addOperation(9, 3)); // Output: 12
console.log(subOperation(9, 3)); // Output: 6
console.log(multiOperation(9, 3)); // Output: 27
console.log(divOperation(9, 3)); // Output: 3
```

As you can see above, we obtained the returned function and assigned it to a variable, as discussed earlier, and we achieved our desired results.

I hope that with the concepts we've explored, you now have a solid understanding of first-class functions and higher-order functions.

Additionally, while learning this concept, I wondered: Can we have more than one higher-order function in a single nested function? The answer is yes. If the function we're passing as an argument also takes another function as an argument, then it, too, can be considered a higher-order function.

Let's look at an example:

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

Above, we have a higher-order function where we pass an operator function as an argument. Inside this higher-order function, there's a nested higher-order function that also takes the operator as an argument. This shows that it's possible to have multiple higher-order functions within a single nested function.

Now, let's move on to the final aspect of first-class functions: the ability to **store functions in arrays and objects**.

Storing functions in arrays and objects can be useful. For example, let's consider storing various arithmetic operation functions in an array and accessing them as needed.

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
const operationFunc = [addition, subtraction, multiplication, division];

// Accessing and using functions from the array
const result1 = operationFunc[0](5, 3); // Addition
const result2 = operationFunc[1](8, 2); // Subtraction

console.log(result1); // Output: 8 (5 + 3)
console.log(result2); // Output: 6 (8 - 2)
```

Likewise, you can store functions as parts of objects to create methods. For instance, let's build an object named `calculation` with methods for addition, subtraction, multiplication, and division. This allows us to perform calculations directly using the object.

```javascript
// Object with calculation methods
const calculation = {
   add: function (num1, num2) {
      return num1 + num2;
   },
   sub: function (num1, num2) {
      return num1 - num2;
   },
   multi: function (num1, num2) {
      return num1 * num2;
   },
   div: function (num1, num2) {
      return num1 / num2;
   }
};

// Using methods from the calculation object
const sum = calculation.add(5, 3);
const difference = calculation.sub(8, 2);

console.log(sum); // Output: 8
console.log(difference); // Output: 6
```

I hope you now have a clear understanding of **first-class functions** and **higher-order functions**. Please share your thoughts and any suggestions for improvement. Thank you!