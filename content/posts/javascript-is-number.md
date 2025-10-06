---
title: "Javascript: What is a number?"
date: 2025-10-06T06:00:00+02:00
draft: false
tags:
  ["javascript", "software development"]
---

Check if a value is a number? Simple task. Just do `!isNaN()`, right? Wrong!

Assume we get an object that has multiple properties. For arguments sake, let's say they might deliver
numbers in integer or float and we need to parse them as
numbers and they deliver other data of various types. It could be:
```javascript
{ myNum: 1, value: "1", someVal: 1.5,  a: true, b: [], c: NaN}
```

Can we use `isNumber()` function? We could, but unfortunately it does not exist (yet)?

Can we `!isNaN()` function? Maybe. But we might get some interesting results. 

Let's look at them:

```
!isNaN test
✓ !isNaN():  42
✓ !isNaN():  3.14
✓ !isNaN():  -5
✓ !isNaN():  -2.7
✓ !isNaN():  0
✗ !isNaN():  NaN
✓ !isNaN():  Infinity
✓ !isNaN():  "123"
✓ !isNaN():  true
✓ !isNaN():  false
✓ !isNaN():  null
✗ !isNaN():  "hello"
✓ !isNaN():  []
```

As we can see it does a pretty good job. Let's start with the good.
- It handles both integers and floats (decimal numbers).
- It handles negatives.
- It handles zero.
- It handles NaN correctly.
- It correctly knows that `"hello"` is not a number.
But here comes the bad:
- It thinks the boolean value `true` and `false` are numbers.
- It thinks `null` type is a number.
- It thinks `"123"` is a number. But it is in fact a string that happens to contain just numbers.
- It thinks an empty array `[]` is a number.

But why? Why is `true` a number?

This might be surprising to some of you. But it is for the same reason that
`"123"` is considered a number. It all has to do with a thing in javacript called
type coercion. The simplest example that comes is:
```javascript
return 3 + "6"
```
What do you think it will return? You might think it returns a type number and the value of `9`.
Good guess. But wrong.
It will return a string: "36"
In either of the possibilities JavaScript would have to *coerce* both of the types to a singular type, a primitive.
This is called type coercion.
If I open the Node.js console I can see this in effect (I am adding a + to coerce it):
```
> +true
1
> +false
0
> +[]
0
```
`true` becomes `1`, `false` becomes `0` and and empty array becomes `0`

Now that that is out of the way how about Number.isInteger()

```
Number.isInteger test
✓ Number.isInteger():  42
✗ Number.isInteger():  3.14
✓ Number.isInteger():  -5
✗ Number.isInteger():  -2.7
✓ Number.isInteger():  0
✗ Number.isInteger():  NaN
✗ Number.isInteger():  Infinity
✗ Number.isInteger():  "123"
✗ Number.isInteger():  true
✗ Number.isInteger():  false
✗ Number.isInteger():  null
✗ Number.isInteger():  "hello"
✗ Number.isInteger():  []

```

It does a pretty good job at restricting our values. But a bit too good.
As the name suggest, it is testing if a value is an integer and therefore
ignoring our floats.

How about `Number.isNaN`

```
!Number.isNaN test
✓ !Number.isNaN():  42
✓ !Number.isNaN():  3.14
✓ !Number.isNaN():  -5
✓ !Number.isNaN():  -2.7
✓ !Number.isNaN():  0
✗ !Number.isNaN():  NaN
✓ !Number.isNaN():  Infinity
✓ !Number.isNaN():  "123"
✓ !Number.isNaN():  true
✓ !Number.isNaN():  false
✓ !Number.isNaN():  null
✓ !Number.isNaN():  "hello"
✓ !Number.isNaN():  []
```

This one is unfortunately even more permissive. Even `"hello"` is true. Why is that?
Because `Number.isNaN` is stricter than `isNaN`? It literally only says true to `NaN`.
E.g. if I put this in the console:
```
> console.log(Number.isNaN(0/0))
true
```
Zero divided by zero in JavaScript returns `NaN`.

So where do we go from here? We roll our own.

```javascript
function isNumber(num) {
    return !isNaN(num) && typeof num === "number";
}
```
Results:
```
isNumber test
✓ isNumber():  42
✓ isNumber():  3.14
✓ isNumber():  -5
✓ isNumber():  -2.7
✓ isNumber():  0
✗ isNumber():  NaN
✓ isNumber():  Infinity
✗ isNumber():  "123"
✗ isNumber():  true
✗ isNumber():  false
✗ isNumber():  null
✗ isNumber():  "hello"
✗ isNumber():  []
```

Looks perfect. Only numbers are regarded as numbers. Why this works?
Simply put we check that the value is of type `number` and we use isNaN to make
sure we don't include `NaN` values. Because in JavaScript land `Not a Number` aka `NaN` is a number.

Why is a `NaN` a number? Or rather why does `typeof NaN === number`?

SPECULATION TIME!!! `typeof` gets us the primitive type of a JavaScript variable. We don't have many
they didn't want to create a new one. Hence, not a number is a number :D

This is the test code I rant to create the results you saw above (I have formatted it slightly for legibility):
```javascript
const assert = require('assert');

function testFunc(func, val, message ) {
  try {
    assert.strictEqual(func, true);
    console.log('\x1b[32m✓\x1b[0m', `${message}:  ${val}`);
  } catch (error) {
    console.log('\x1b[31m✗\x1b[0m', `${message}:  ${val}`);
    // throw error;
  }
}

function isNumber(num) {
    return !isNaN(num) && typeof num === "number";
}

// Examples
const testValues = [42, 3.14, -5, -2.7, 0, NaN, Infinity, "123", true, false, null, "hello", []];

// !isNaN

console.log("!isNaN test")
testValues.forEach(val => {
  testFunc(!isNaN(val), val, "!isNaN()")
});

// Number.isInteger
console.log("")
console.log("Number.isInteger test")
testValues.forEach(val => {
  testFunc(Number.isInteger(val), val, "Number.isInteger()")
});

// Number.isInteger
console.log("")
console.log("!Number.isNaN test")
testValues.forEach(val => {
  testFunc(!Number.isNaN(val), val, "!Number.isNaN()")
});

// isNumber
console.log("")
console.log("isNumber test")
testValues.forEach(val => {
  testFunc(isNumber(val), val, "isNumber()")
});
```
