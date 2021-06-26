
eloquent js: chapters 1-6, 10, 11, 15, 20;

# Chapter 3: *functions*

- ## Arrow Functions
d: another way to write functions, coming back to this in chapter 5
syntax:
```js
let power = (x, y) => { //do something };
```
or
```js
let power = (x) => { //do something };
```
or
```js
let power = x => //do something;
```

- ## Optional Arguments
note: when passing multiple arguements through a function that takes less than passed, JS will ignore the extra ex.
```js
function square(x) { return x * x; }
console.log(square(4, true, "hedgehog"));
// → 16, true and "hedgehog" are ignored completely
```
note: this also works for passing less arguments than parameters ex.
```js
function minus(a, b) {
  if (b === undefined) return -a;
  else return a - b;
}

console.log(minus(10));
// → -10
console.log(minus(10, 5));
// → 5
```
note: setting defaults looks like (= value) after setting parameter in function signature ex.
```js
function minus(a, b = 2) {
  return a - b;
}

console.log(minus(10));
// → 8
```
# Chapter 4: *Data Structures - Objects and Arrays*


- ## Objects
d: values of type *object* are arbitrary collections of properties.
```js
let food = {
    meat : ["chicken", "beef", "lamb"],
    cheese : true
};
```
*delete*: will remove a property from an object ex.  
*in*: looks inside of object for property
```js
let anObject = {left: 1, right: 2};
console.log(anObject.left);
// → 1
delete anObject.left;
console.log(anObject.left);
// → undefined
console.log("left" in anObject);
// → false
console.log("right" in anObject);
// → true
```
*Object.keys*: returns an array of strings of the property names
```js
let objectA = {a: 1, b: 2};
console.log(Object.keys(objectA));
// → ["a", "b"]
```
*Object.assign*: copies all properties from one object into another
```js
let objectA = {a: 1, b: 2};
Object.assign(objectA, {b: 3, c: 4});
console.log(objectA);
// → {a: 1, b: 3, c: 4}
```
note: setting objects to the same value does not equal having an object equal to another ex.
```js
let object1 = {a: 1};
let object2 = object1;
let object3 = {a: 1};
// → object1 == object 2
// → object1 != object 3
```
- ## Arrays
*push*: adds element to the end of array and increases length by 1.
```js
a.push(7);
// → [1,3] = [1,3,7]
```
*pop*: removes last element in array ex.
```js
a.pop(7);
// → [1,3,7] = [1,3]
```
*unshift*: adds element at beginning of array and increases length by 1 ex.
```js
a.unshift(9);
// → [1,3] = [9,1,3]
```
*shift*: removes first element in array ex.
```js
a.shift();
// → [1,3] = [3]
```
*concat*: combines two arrays into one new array ex.
```js
a.concat(b);
// → a = [1,3], b = [2,4]
// → a.concat(b) = [1,3,2,4]
```
*includes*: checks whether given value exists in an array ex.
```js
function doSomething(event) {
    let entry = {events: 1}
    let index = 0;
    if (entry.events.includes(event)) index += 1;
}
// → index = 1 if doSomething(1); is called because our entry object's event property is included
```
note: first code box is a classic way of iterating over each element in a for loop, second code box is a JavaScript specific simplier way to write this type of for loop     
 
*of*: in a loop, it will loop over all elements in the value given after. works in arrays, strings, and some other data structures, resumed in chapter 6. ex.
```js
//1 code box
for (let i = 0; i < JOURNAL.length; i++) {
  let entry = JOURNAL[i];
  // Do something with entry
}
```
```js
//2nd code box
for (let entry of JOURNAL) {
  console.log(`${entry.events.length} events.`);
}
```
*indexOf*: searches array and returns value passed.
*lastIndexOf*: searched array from back to front and returns value passed.

note: both indexOf and lastIndexOf take optional second argument for starting point.
```js
console.log([1, 2, 3, 2, 1].indexOf(2));
// → 1
console.log([1, 2, 3, 2, 1].lastIndexOf(2));
// → 3
```








