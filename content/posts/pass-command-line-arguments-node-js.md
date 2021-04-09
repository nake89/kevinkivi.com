---
title: 'How to pass command-line arguments in node.js'
date: Sat, 15 Apr 2017 16:43:25 +0000
draft: false
tags: ['Code', 'Guides']
---

So you want to pass information to your program. This can be quite easily achieved. The arguments are contained in `process.argv`. arg.js
```javascript
console.log(process.argv[0]);
console.log(process.argv[1]);
console.log(process.argv[2]);
console.log(process.argv[3]);
console.log(process.argv[4]);
```
Testing the code:
```
nake89@debian:~/nodeprojects/soacomp$ node arg.js what is this
/home/nake89/.nvm/versions/node/v6.10.2/bin/node
/home/nake89/nodeprojects/soacomp/arg.js
what
is
this
```
So the first line is the location of your node executable and the second one is the location of the script. These are largely unnecessary which is why the following script is so popular. It strips away the first to results of the array.
```javascript
var args = process.argv.slice(2);
```
args.js
```javascript
var args = process.argv.slice(2);
console.log(args[0]);
console.log(args[1]);
console.log(args[2]);
```
Testing the new code:
```
nake89@debian:~/nodeprojects/soacomp$ node arg.js what is this
what
is
this

```
As you can see the unnecessary parts are removed and you can focus on the arguments you want to manipulate. Happy coding!
