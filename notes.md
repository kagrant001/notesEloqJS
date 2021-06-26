##  REPL
 **-> Read Eval Print Loop**

---

## Datatypes JavaScript:
- primative: *numbers, strings, booleans*
- Object: *objects, functions*        
- Null

undefined = absence of value

## Falsy Values:
*undefined; null; 0; NaN; ""*


## Objects: 
**are not class based like java or c, instead is prototype based**

object declaration:
```
let Car = { color: "red", model: "ford"};
//where color and model are properties
```
```
let Car = {}; //<-- object with no properties
```
```
let x = Object.create(null); //<-- null is there b/c must pass arg
```

## Arrays:

```
myArray["5"] = "abc";
```


- *can hold different types*
- *acts more like ArrayList from java*
- *can set value to position in future w/o populating the rest => sparce array i.e. ["zero", undefined*7, "ten"]*


## JSON -> JavaScript Object Notation



---
eloquent js: chapters 1-6, 10, 11, 15, 20;

# Chapter 3: *functions*

- ### Arrow Functions
d: another way to write functions, coming back to this in chapter 5
syntax:
```
let power = (x, y) => { //do something };
```
or
```
let power = (x) => { //do something };
```
or
```
let power = x => //do something;
```

- ### Optional Arguments
note: when passing multiple arguements through a function that takes less than passed, JS will ignore the extra ex.
```
function square(x) { return x * x; }
console.log(square(4, true, "hedgehog"));
// → 16, true and "hedgehog" are ignored completely
```
note: this also works for passing less arguments than parameters ex.
```
function minus(a, b) {
  if (b === undefined) return -a;
  else return a - b;
}

console.log(minus(10));
// → -10
console.log(minus(10, 5));
// → 5
```













