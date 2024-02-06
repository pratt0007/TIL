# JAVA SCRIPT
- Null -> Object
- Baki sab me datatype

```JS
let score = "33abc"
console. log (typeof score);
console. log ( ty peof (score) ) ;
let valueinnumber = Number(score)
console. log (typeof valuelnNumber) ;
console. log (valueinnumber) ;
For this the console.log(score) will show NaN
and if the score is NULL then it will show 0
```
```JS
console. log ("1")
console. log(l + "2")
console. log ("1" + 2 + 2) -> NO ADD 2 + 2
console. log(l + 2 + "2") -> ADD 2 + 2 AND THEN STRING ADD 3
o/p->
1
12
122
32
```
```JS
console. log(null > 0);
console. log( null == 0);
console. log(null >= 0);

op->
false
false
true

Some conversion are Null to NAN some operator converts to 0

```
- Stirct check -> (===) -> check same data types as well
- console.log("0" == 0) return TRUE
- console.log("0" === 0) return False

## Type of Memory Structutes
- Stack memory-> primitive-> Call by value
- Heap memory -> Non primitive -> Call by reference -> The change in any of the type will result in change in all as it is stored in heap
![image](https://github.com/pratt0007/TIL/assets/100209212/77d9596b-9d4e-4d71-a97f-fe1cb0e0fc44)

```Js
let a = "hello" -> not an object
const a = new String("hello") -> Object-> can use inbult functions
```
```JS
let a = "hello"
console.log(a)

const b = new String("Hello")
console.log(b)

o/p
hello
[String: 'Hello']
```
- array in JS can store any datatypes in single array.
![image](https://github.com/pratt0007/TIL/assets/100209212/b6573831-e765-4355-9da9-62fd14576d1e)
See this array doent concatinate -> it adds us as whole subarray.
- The 4th element of the array is that array which we pushed.
- if we do concat() -> same output if we print that same array, if we make a new array and console.log() it then we get the concatinated array.

## Object
 ![image](https://github.com/pratt0007/TIL/assets/100209212/2eca499a-694e-40a2-b75f-4272909dde86)
- 2 ways to get the content of an object.
- a) .operator but if we define key as "" strings then we have to call by [] bracket.

## Symbol- 
- In JavaScript, a Symbol is a primitive data type introduced in ECMAScript 6 (ES6).
- It is a unique and immutable data type that can be used as an identifier for object properties.
- Unlike strings or numbers, symbols are guaranteed to be unique, and they help avoid naming conflicts in object properties.

## Functions
- Rest/ Spread operator
- Nested loop me child func ke variables can access parent func ke variables

## This keyword
- If we do console.log(this) inside an object ie -> const objname {}. Then we can fetch value inside
- but if we define function then we cant use this keyword to get the data.

![image](https://github.com/pratt0007/TIL/assets/100209212/003dfcc2-479d-4e17-a146-0f713a970bf4)

