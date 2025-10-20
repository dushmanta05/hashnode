---
title: "How to Use Array.indexOf() for Comparing Multiple Items in JavaScript"
datePublished: Wed Dec 07 2022 17:39:39 GMT+0000 (Coordinated Universal Time)
cuid: clbdxql7m000008ij9w1bcfg3
slug: using-arrayindexof-to-compare-multiple-items-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1760939033858/d505fb90-a841-46c3-b77f-3c799f7bbe33.png
tags: javascript

---

We are all familiar with the **Logical OR Operator** (||). One of the most common uses of the **OR operator** is to compare one value to several other values in a condition.

Let's look at an example:  
Write a function that takes the name of a month as an argument and returns whether that month has 31 days or not.

```javascript
function checkMonth(month)
if (month === 'January' || month === 'March' ||
   month === 'May' || month === 'July' ||
   month === 'August' || month === 'October' || month = 'December') {
   return console.log(`${month} has 31 days.`)
} else {
   return console.log(`${month} doesn't have 31 days.`)
}
checkMonth('July') // 'July has 31 days'
checkMonth('February') // 'February doesn't have 31 days'
```

Here, we are using the **or operator** five times to get the result, and there is repetitive code, which doesn't look clean. When we compare 2 or 3 values using the **or operator**, the code doesn't look too bad. However, as the number of values increases, the code looks messy.

As developers, we should all follow the most important rule for writing code: DRY (Don't Repeat Yourself). Never repeat your code. So, we need to eliminate these repetitive statements, and this is where the `Array.indexOf()` method comes in. Before solving the problem using the `Array.indexOf()` method, let's understand what this method does.

### **Array.indexOf()**

The `.indexOf()` method takes two arguments: the element we are searching for and the index from which we start searching. You can pass either just the first argument or both arguments.

* If we pass the element we are searching for as the only argument, the method will return the first index where the element is found. If the element is not in the array, it will return -1.
    
* If we pass both arguments, this method will search for the given element starting from the specified index in the array.
    

Let's go through some examples for a better understanding:

```javascript
const animals = ['tiger', 'Lion', 'monkey', 'dog', 'cat', 'Lion', 'tiger'];

//passing only one argument
console.log(animals.indexOf('lion')); // output = 1 
console.log(animals.indexOf('cow')) // output = -1

// passing both arguments
console.log(animals.indexOf('lion', 2)); // output = 5
console.log(animals.indexOf('monkey', 3)); // output -1, since element is not present after index 3
```

Now that we understand the `.indexOf()` method, let's rewrite the previous function.

```javascript
function checkMonth(month) {
   const compareMonths = ['January', 'March', 'May', 'July', 'August', 'October', 'December'];

   // we can use ternary instead of if...else
   return compareMonths.indexOf(month) ? `${month} has 31 days` : `${month} doesn't have 31 days`;
}

console.log(checkMonth('July')); // "July has 31 days" 
console.log(checkMonth('February')) // "February doesn't have 31 days"
```

I hope you found this article helpful. For more details about the `indexOf()` method, visit the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf).