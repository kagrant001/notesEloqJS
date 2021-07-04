
eloquent js: chapters 1-6, 10, 11, 15, 20;

# Chapter 3: *functions*

- ## Arrow Functions
d: another way to write functions, coming back to this in chapter 5
syntax:
```js
let power = (x, y) => { /*do something*/ };
```
or
```js
let power = (x) => { /*do something*/ };
```
or
```js
let power = x => /*do something*/;
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
d: values of type ***object*** are arbitrary collections of properties.
```js
let food = {
    meat : ["chicken", "beef", "lamb"],
    cheese : true
};
```
***delete***: will remove a property from an object ex.  
***in***: looks inside of object for property
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
***Object.keys***: returns an array of strings of the property names
```js
let objectA = {a: 1, b: 2};
console.log(Object.keys(objectA));
// → ["a", "b"]
```
***Object.assign***: copies all properties from one object into another
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
***push***: adds element to the end of array and increases length by 1.
```js
a.push(7);
// → [1,3] = [1,3,7]
```
***pop***: removes last element in array ex.
```js
a.pop(7);
// → [1,3,7] = [1,3]
```
***unshift***: adds element at beginning of array and increases length by 1 ex.
```js
a.unshift(9);
// → [1,3] = [9,1,3]
```
***shift***: removes first element in array ex.
```js
a.shift();
// → [1,3] = [3]
```
***concat***: combines two arrays into one new array ex.
```js
a.concat(b);
// → a = [1,3], b = [2,4]
// → a.concat(b) = [1,3,2,4]
```
***slice***: takes start and end indices and returns an array of only the elements between them. if there is no end index, then it will return from start to the end of the whole array ex.
```js
console.log([0, 1, 2, 3, 4].slice(2, 4));
// → [2, 3]
console.log([0, 1, 2, 3, 4].slice(2));
// → [2, 3, 4]
```
***splice***: works as slice, but modifys array based on syntax below    
splice(start)  
splice(start, deleteCount)  
splice(start, deleteCount, item1)  
splice(start, deleteCount, item1, item2, itemN)  
```js
let months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, 'May');
// replaces 1 element at index 4
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "May"]

months.splice(2, 1);
console.log(months);
// expected output: Array ["Jan", "Feb", "April", "May"]
```
***includes***: checks whether given value exists in an array ex.
```js
function doSomething(event) {
    let entry = {events: 1}
    let index = 0;
    if (entry.events.includes(event)) index += 1;
}
// → index = 1 if doSomething(1); is called because our entry object's event property is included
```
note: first code box is a classic way of iterating over each element in a for loop, second code box is a JavaScript specific simplier way to write this type of for loop     
 
***of***: in a loop, it will loop over all elements in the value given after. works in arrays, strings, and some other data structures, resumed in chapter 6. ex.
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
***for each - arrays***: for each element in an array do something
```js
let array1 = [1,2,3];
array1.forEach(element => console.log(element));
// → 1
// → 2
// → 3
```

***indexOf***: searches array and returns value passed.

***lastIndexOf***: searched array from back to front and returns value passed.

note: both indexOf and lastIndexOf take optional second argument for starting point.
```js
console.log([1, 2, 3, 2, 1].indexOf(2));
// → 1
console.log([1, 2, 3, 2, 1].lastIndexOf(2));
// → 3
```
- ## Rest Parameters
d: sometimes it can be useful to have a function take infinite parameters  
note: putting ... before the last variable allows this ex.  
```js
function max (...numbers) { //do something};
console.log(max(1,3,6,2,9));
// (assuming function max returned the max) → 9
```
note: this can be applied to arrays too ex.
```js
let numbers = [5, 1, 7];
console.log(max(...numbers));
// → 7
```
or
```js
let words = ["never", "fully"];
console.log(["will", ...words, "understand"]);
// → ["will", "never", "fully", "understand"]
```

- ## JSON
d: JavaScript Object Notation. This is a format for declaring properties in an object ex.
```js
{
  "squirrel": false,
  "events": ["work", "touched tree", "pizza", "running"]
}
```
***JSON.stringify***: converts data into JSON encoded string ex.
```js
let string = JSON.stringify({squirrel: false, events: ["weekend"]});
console.log(string);
// → {"squirrel":false,"events":["weekend"]}
```
***JSON.parse***: converts data from JSON encoded string into the value it encodes ex.
```js
console.log(JSON.parse(string).events);
// → ["weekend"]
```

# Chapter 4 Exercises:

- ## The sum of a range
```js
function range(start, end) {
  let nums = [];
  if (start < end) {
  	for (let i=start; i <= end; i++) {
      nums.push(i);
    }
    return nums;
  } else if (start > end) {
    for (let i=start; i >= end; i--) {
      nums.push(i);
    }
    return nums;
  }  
}

function sum(numbers) {
  let totalSum = 0;
  numbers.forEach(element => totalSum += element);
  return totalSum;
}

console.log(range(1, 10));
// → [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
console.log(range(5, 2, -1));
// → [5, 4, 3, 2]
console.log(sum(range(1, 10)));
// → 55
```

- ## Reversing an array
```js
function reverseArray(array) {
  let newArray = [];
  let temp = array.length - 1;
  for (let i=0; i<array.length; i++) {
    newArray[i] = array[temp];
    temp--;
  }
  return newArray;
}

function reverseArrayInPlace(array) {
  let tempHolder;
  let backwardsCounter = array.length-1;
  for (let i=0; i<array.length/2; i++) {
    tempHolder = array[i];
    array[i] = array[backwardsCounter];
    array[backwardsCounter] = tempHolder;
    backwardsCounter--;
  }
  return array;
}

console.log(reverseArray(["A", "B", "C"]));
// → ["C", "B", "A"];
let arrayValue = [1, 2, 3, 4, 5];
reverseArrayInPlace(arrayValue);
console.log(arrayValue);
// → [5, 4, 3, 2, 1]
```

- ## A List
```js
function arrayToList(arr) {
  let list = null;
  //start from the back because the first thing put in the list is the 
  //last value out hence start at the last value
  for (let i=arr.length-1; i>=0; i--) {
    list = {
      value: arr[i],
      //iterate through the list (recursive)
      rest: list};
  }
  return list;
}

function listToArray(list) {
  let arr = [];
  //using tempList since its better to not iterate through the original one
  let tempList = list;
  //runs until reaches end of list since the end of list is dictated
  //by the value == null
  while(tempList.rest != null) {
    arr.push(tempList.value);
    //how to iterate through a list
    tempList = tempList.rest;
  }
  //last value is being left off since in the while loop the rest value
  //couldnt continue
  arr.push(tempList.value);
  return arr;
}

function prepend(element, list) {
  let tempList = list;
  
  list = {
    value: element,
    rest: tempList};

  return list;
}

function nth(list, number) {
  let counter = 0;
  //every iteration, node points to current list properties. then at the end of iteration, node moves on to the next set of list properties. when node is null, there are no values to access so the loop is done.
  
  for (let node = list; node; node = node.rest) {
    if (counter == number) {
	  return node.value;
    } else {
      counter++;
    }
  }  
}

console.log(arrayToList([10, 20]));
// → {value: 10, rest: {value: 20, rest: null}}
console.log(listToArray(arrayToList([10, 20, 30])));
// → [10, 20, 30]
console.log(prepend(10, prepend(20, null)));
// → {value: 10, rest: {value: 20, rest: null}}
console.log(nth(arrayToList([10, 20, 30]), 1));
// → 20

```


# Chapter 5: *Higher-Order Functions*

- ## Higher-Order Functions
d: functions that operate on other functions i.e. taking in a function as a parameter or returning a function call

note: higher-order functions allow abstraction (using calls to simplify lines of code) of actions.

example 1: functions that create new functions (using arrow function notation)
```js
function greaterThan(n) {
  return m => m > n;
}
let greaterThan10 = greaterThan(10);
console.log(greaterThan10(11));
// → true
```
example 2: functions that provide new control flow (calling other methods such as then();)
```js
function unless(test, then) {
  if (!test) then();
}

repeat(3, n => {
  unless(n % 2 == 1, () => {
    console.log(n, "is even");
  });
});
// → 0 is even
// → 2 is even
```

note: the array method forEach from chapter 4, works as a higher order function

example 3ish: when later calling the function ***filter***, for this case, the test parameter will need to be a function (which is possible in JS). This adds reusablilty by allowing other calls use their own test function → abstraction ;)
```js
function filter(array, test) {
//do something
}
```

- ## More Array Methods
note: all of these methods are standard methods that can be called like array.filter() or array.map() with respective parameters

***filter***: this method will filter out all elements in an array that doesnt pass the test function.  
```js
//native code
let passed = [];
  for (let element of array) {
    if (test(element)) {
      passed.push(element);
    }
  }
  return passed;
}

//normal use example →

//filter through array testing if the element is equal to "hello"
let filter1 = array1.filter(x => x == "hello");
```
***map***: this method will transform an array by applying the function parameter to each element in a new array and returning it.  
```js
//native code
function map(array, transform) {
  let mapped = [];
  for (let element of array) {
    mapped.push(transform(element));
  }
  return mapped;
}
//normal use example →

//map through the array by changing each element to the current element times 2
let map1 = array1.map(x => x * 2);
```
***reduce***: this method builds a value by combining an element from the array with the current value, returning the combined value from the entire array.  
```js
//native code
function reduce(array, combine, start) {
  let current = start;
  for (let element of array) {
    current = combine(current, element);
  }
  return current;
}

//normal use example → 

//add each element in the array with the current value
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10
```
note: "You can usually afford the readable approach, but if you’re processing huge arrays, and doing so many times, the less abstract style might be worth the extra speed."

# Chapter 5 Exercises: 
- ## Your Own Loop
```js
//test, update, and body are function parameters
function loop(value, test, update, body) {
  while(test(value)) {
    body(value);
    value = update(value);
  }
}

loop(3, n => n > 0, n => n - 1, console.log);
// → 3
// → 2
// → 1
```
# Chapter 6: *The Secret Life of Objects*

- ## Prototypes
d: the object, array, or function that acts as a fall back source of an object, array, or function when it is requested for a property it does not have. Prototypes can use other objects, arrays, or functions as their prototype, but will always have an original prototype which is something like Object.prototype(Object1).

***Object.getPrototypeOf()***: returns the prototype of an object.
```js
Object.getPrototypeOf(Object1) 
// → returns Object1's prototype
```
***Object.create()***: creates an object with a specific prototype
```js
let protoRabbit = {
  speak(line) {
    console.log(`The ${this.type} rabbit says '${line}'`);
  }
};
let killerRabbit = Object.create(protoRabbit);
killerRabbit.type = "killer";
killerRabbit.speak("SKREEEE!");
// → The killer rabbit says 'SKREEEE!'
```
note: assume protoRabbit has multiple properties to show the complexities that make up a rabbit, the killerRabbit class object is inheriting all of the features (saving time and code to remake all of them) and then changing some of the features to make it more fit.

- ## Classes

note: JS does not really have formal class structures like other languages such as java, prototypes are useful for inheritence since there is no structure for classes.

***constructor functions in JS*:**
```js
function makeRabbit(type) {
  let rabbit = Object.create(protoRabbit);
  rabbit.type = type;
  return rabbit;
}
```
note: when makeing a new rabbit, if using the ***new*** keyword, the object with the right prototype will be created, will be bounded to the ***this*** in the constructor, and then will be returned at the end. this is simply another way of making a constructor.
```js
//constructor
function Rabbit(type) {
  this.type = type;
}

//initialization
let weirdRabbit = new Rabbit("weird");
```

- ## Class Notation:

note: jk, now JS has class declaration
```js
class Rabbit {
  constructor(type) {
    this.type = type;
  }
  speak(line) {
    console.log(`The ${this.type} rabbit says '${line}'`);
  }
}

let killerRabbit = new Rabbit("killer");
let blackRabbit = new Rabbit("black");
```
note: currently, class declarations only allow methods (properties that hold functions). this can be annoying when you want to store non-function data since u cant ;)

- ## Maps
d: (Exclaimer) this is not the same this as array.map(). this is a programming construct. a map is a data structure that associates its values (keys) with other values.

```js
//an example of a simple map in an object
let ages = {
  Boris: 39,
  Liang: 22,
  Julia: 62
};
```
note: objects are not the best place to use maps since objects are derived from Object.prototype meaning properties like toString are always present in the map ex.
```js
//continued from code above
console.log("Is toString's age known?", "toString" in ages);
// → Is toString's age known? true
```
note: Object property names need to be String and when you cannot convert keys to type to String (aka objects), you cannot use objects as maps. so JS made a class for maps called Map(); which allows any type as keys ex.
```js 
let ages = new Map();
ages.set("Boris", 39);
ages.set("Liang", 22);
ages.set("Júlia", 62);
```
note: the methods ***set***, ***get***, and ***has*** are all apart of the Map class and work as a setter, getter, and contains function.

- ## The Iterator Interface
d: iterators just iterate a given thing. in JS its most common to iterate arrays but you can also iterate objects. in order to iterate objects, it must have a property with a ***Symbol.iterator*** key.
```js
//example of simple iterator
let okIterator = "OK"[Symbol.iterator]();
console.log(okIterator.next());
// → {value: "O", done: false}
console.log(okIterator.next());
// → {value: "K", done: false}
console.log(okIterator.next());
// → {value: undefined, done: true}
```
note: iterators have two properties, ***value*** and ***done***. ***value*** is what is being iterated through and the value that is supposed to be returned. ***done*** is a boolean representing if we have iterated through whatever we are iterating through completely or not.
```js
//full example of an iterator

//class Matrix is built to represent a 2D array
class Matrix {
  constructor(width, height, element = (x, y) => undefined) {
    this.width = width;
    this.height = height;
    this.content = [];

    for (let y = 0; y < height; y++) {
      for (let x = 0; x < width; x++) {
        this.content[y * width + x] = element(x, y);
      }
    }
  }

  get(x, y) {
    return this.content[y * this.width + x];
  }
  set(x, y, value) {
    this.content[y * this.width + x] = value;
  }
}

//MatrixIterator will produce objects with the x, y, and value properties of Matrix
class MatrixIterator {
  constructor(matrix) {
    this.x = 0;
    this.y = 0;
    this.matrix = matrix;
  }

  //next() is what will be called to iterate to the next element; this is what makes an Iterator an Iterator
  next() {
    //this will run if the martix has iterated completely
    if (this.y == this.matrix.height) return {done: true};

    let value = {x: this.x,
                 y: this.y,
                 //using getter from matrix class
                 value: this.matrix.get(this.x, this.y)};
    this.x++;
    //once done with a row, start a new row with y++ and reset x
    if (this.x == this.matrix.width) {
      this.x = 0;
      this.y++;
    }
    //basically saying: not done, so iterate again, but heres the value
    return {value, done: false};
  }
}

//because we are adding Symbol.iterator to the Matrix prototype, we can now loop over the Matrix class with for/of
Matrix.prototype[Symbol.iterator] = function() {
  return new MatrixIterator(this);
};

//example of iterating a Matrix with for/of
let matrix = new Matrix(2, 2, (x, y) => `value ${x},${y}`);
for (let {x, y, value} of matrix) {
  console.log(x, y, value);
}
// → 0 0 value 0,0
// → 1 0 value 1,0
// → 0 1 value 0,1
// → 1 1 value 1,1
```

- ## Getters, Setters, and Statics
note: getters and setters have actual syntax in JS similar to how constructor does too. (they still work the same as normal getters and setters though so dont worry).
```js
class Temperature {
  constructor(celsius) {
    this.celsius = celsius;
  }
  get fahrenheit() {
    return this.celsius * 1.8 + 32;
  }
  set fahrenheit(value) {
    this.celsius = (value - 32) / 1.8;
  }
}
```
note: when ***static*** is put in front of a method name, it means that the method is going to be stored inside of the constructor of the class. 
```js
//assume that this is inside the code above
static fromFahrenheit(value) {
    return new Temperature((value - 32) / 1.8);
}
```
note: (in this case) writing ***Temperature.fromFahrenheit(100)*** will allow you to make a Temerature in degrees fahrenheit.

- ## Inheritance
d: in JS, prototypes are already kind of like inheritance for objects. however, when wanting to build a class based on a different class an approach that implements parent and child functions is using ***extends***.   

***extends***: indicates that a class should be based on a class other than the default Object prototype. the class it will be based on (in this case Matrix) will be refered to as the *superclass* and this class will be refered to as the *subclass*.
```js
class SymmetricMatrix extends Matrix {
  constructor(size, element = (x, y) => undefined) {
    //super keyword is calling the superclass's constructor to act as the constructor for the subclass SymmetricMatrix
    super(size, size, (x, y) => {
      //this is adding new features in the constructor which is totally acceptable
      if (x < y) return element(y, x);
      else return element(x, y);
    });
  }

  set(x, y, value) {
    //super keyword in this case is refering to the set method from the superclass Matrix. we want to redefine set for the subclass but also want to use the original behavior.
    super.set(x, y, value);
    if (x != y) {
      super.set(y, x, value);
    }
  }
}
```

- # The Instanceof Operator
d: this is used to know whether an object was derived from a specific class
```js
console.log(
  new SymmetricMatrix(2) instanceof SymmetricMatrix);
// → true
console.log(new SymmetricMatrix(2) instanceof Matrix);
// → true
console.log(new Matrix(2, 2) instanceof SymmetricMatrix);
// → false
console.log([1] instanceof Array);
// → true
```
note: can be applied to stardard objects like arrays as example 4

# Chapter 6 Exercises: 
- ## A Vector Type
```js
class Vec {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
  
  plus(vec2) {
    let plusX = this.x + vec2.getX();
    let plusY = this.y + vec2.getY();
    return new Vec(plusX, plusY);
  }
  
  minus(vec2) {
    let minusX = this.x - vec2.getX();
    let minusY = this.y - vec2.getY();
    return new Vec(minusX, minusY);
  }
  
  length() {
    let distance = Math.sqrt(((this.x * this.x) + (this.y * this.y)));
    return distance;
  }
  
  getX() {
    return this.x;
  }
  
  getY() {
    return this.y;
  }
}

console.log(new Vec(1, 2).plus(new Vec(2, 3)));
// → Vec{x: 3, y: 5}
console.log(new Vec(1, 2).minus(new Vec(2, 3)));
// → Vec{x: -1, y: -1}
console.log(new Vec(3, 4).length());
// → 5
```

- ## Groups
```js
class Group {
  constructor(groupMembers) {
    //its okay to set this group to size 0 since we will push members in later, increasing the size by 1 to fit them in
    this.groupMembers = [];
  }
  
  add(newMember) {
    //conditon is that a certain member can only be in the group once
    if (!(this.has(newMember))) {
      this.groupMembers.push(newMember);
    } else {
      console.log("this member is already in the group");
    }
  }
  
  delete(member) {
    //condition is that the member must be in the group before being deleted
    if (this.has(member)) {
      let index = this.groupMembers.indexOf(member);
      this.groupMembers.splice(index, 1);
    } else {
      console.log("this member was previously not in this group");
    }
  }
  
  has(member) {
    return this.groupMembers.includes(member);      
  }
  
  static from(arg) {
    let isIterable = false;
    //checking if our arg is null or undefined, then checks if the type of the Symbol.iterator of arg is equal to a function since the value is a zero-argument FUNCTION that will return an object
    if (arg == null) {
      isIterable = false;
    } else if (typeof arg[Symbol.iterator] === 'function') {
      isIterable = true;
    }
    
    if (isIterable) {
      let newGroup = new Group();
      for (let element of arg) {
		newGroup.add(element);
      }
      return newGroup;
    }
  }
}

let group = Group.from([10, 20]);
console.log(group);
console.log(group.has(10));
// → true
console.log(group.has(30));
// → false
group.add(10);
// → "this member is already in the group"
group.delete(10);
console.log(group.has(10));
// → false
```

- ## Iterable Groups
```js
class Group {
  constructor(groupMembers) {
    this.groupMembers = [];
  }
  
  add(newMember) {
    if (!(this.has(newMember))) {
      this.groupMembers.push(newMember);
    } else {
      console.log("this member has already been added");
    }
  }
  
  delete(member) {
    if (this.has(member)) {
      let index = this.groupMembers.indexOf(member);
      this.groupMembers.splice(index, 1);
    } else {
      console.log("this member was previously not in this group");
    }
  }
  
  has(member) {
    return this.groupMembers.includes(member);      
  }
  
  static from(arg) {   
    //no need to call Symbol.iterator() as it doesnt iterate through for us, all its doing is making it readable for later use such as here where we are using a for/of loop
    let newGroup = new Group();
      for (let element of arg) {
		newGroup.add(element);
      }
    
    return newGroup;    
  }
  
  [Symbol.iterator]() {
    return new groupIterator(this);
  }
}

//all this class is doing is making data passed into group readable for a for/of loop, not actually iterating through an object and doing x,y,z with it
class groupIterator {
  constructor(group) {
    //x is a property that tracks position
    this.x = 0;
    this.group = group;
  }
  
  next() {
    if (this.x == this.group.groupMembers.length) return {done: true};
    
    //dont do this because its creating a nested object:
    //let value = {value: this.group.groupMembers[this.x]};
    //this.x++;
    //return {value, done: false};
    
    //instead do this
    let value = {value: this.group.groupMembers[this.x], done:false};
    this.x++;
    
    return value
  }
}

for (let value of Group.from(["a", "b", "c"])) {
  console.log(value);
}
// → a
// → b
// → c
```