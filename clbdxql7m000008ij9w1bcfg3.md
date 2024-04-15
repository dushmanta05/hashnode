---
title: "Using Array.indexOf() to compare multiple items in JavaScript"
datePublished: Wed Dec 07 2022 17:39:39 GMT+0000 (Coordinated Universal Time)
cuid: clbdxql7m000008ij9w1bcfg3
slug: using-arrayindexof-to-compare-multiple-items-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695193413873/aea70281-9d1e-45a3-86f2-ba288b1a40eb.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695193433570/fff2f569-4d71-4cd0-9793-e43c9a816843.webp
tags: javascript

---

We are all familiar with the **Logical OR Operator** (||). One of the most common uses of the **OR operator** is when we specify a condition by comparing one value to several other values.

Let's take an example:  
Write a function that takes the month name as an argument and returns whether that month has 31 days or not.

```javascript
function checkMonth(month)
    if ( month === 'January' || month === 'March' || 
    month === 'May' || month === 'July' || 
    month === 'August' || month === 'October' || month = 'December'){
        return console.log(`${month} has 31 days.`)
    } else {
        return console.log(`${month} doesn't have 31 days.`)
    }
checkMonth('July') // 'July has 31 days'
checkMonth('February') // 'February doesn't have 31 days'
```

Here we are using the **or operator** five times to get the result, and there is also repeatable code, which doesn't look clean. When we compare 2 or 3 values using the **or operator**, the code doesn't look that bad, but when the number of compared values increases, it looks very poor.

As a developer, everyone should be aware of the most important rule (I call it the **platinum rule**) for writing code, which is DRY (do not repeat your) code. I repeat: never repeat your code. So here we've got to eliminate these repetitive statements and this is where the **Array.indexOf()** method comes in. Before solving the problem using **Array.indexOf()** method, let's dive into what this method does.

### **Array.indexOf()**

The .indexOf() method takes two arguments: the element we're searching for and the index from which we're searching forward. You have to pass the first argument or both arguments.

* If we pass the searched element as the only argument, then if the searched element is present in the given array, this method will return the first index at which the element is present, or it'll return -1 if the element is not present in that array.
    
* If we pass both arguments, then this method will search for the presence of the given element from the index we've passed in that array.
    

Let's look through some examples for a better understanding:

```javascript
const animals = ['tiger', 'Lion', 'monkey', 'dog', 'cat', 'Lion', 'tiger'];

//passing only one argument
console.log(animals.indexOf('lion')); // output = 1 
console.log(animals.indexOf('cow')) // output = -1

// passing both arguments
console.log(animals.indexOf('lion', 2)); // output = 5
console.log(animals.indexOf('monkey', 3)); // output -1, since element is not present after index 3
```

Now that we've learned about the .**indexOf()** method, let's rewrite the preceding function.

```javascript
function checkMonth (month) {
const compareMonths = ['January', 'March', 'May', 'July', 'August', 'October', 'December'];

// we can use ternary instead of if...else
return compareMonths.indexOf(month) ? `${month} has 31 days` : `${month} doesn't have 31 days`;
}

console.log(checkMonth('July')); // "July has 31 days" 
console.log(checkMonth('February')) // "February doesn't have 31 days"
```

I hope you found this article helpful. For more details about the **indexOf()** method, visit the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf).