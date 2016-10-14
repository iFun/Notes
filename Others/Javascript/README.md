# JavaScript

## Tricks

* Optional Callback
   - typeof callback === 'function' && callback();
* Remove property from a javascript object
   - Delete is the only true way to remove object's properties without any leftovers, but it works ~ 100 times slower compared to its "alternative", setting _object[key] = undefined_.
   - Use delete when you are passing the result object to the code on which you don't have control (or when you are not sure about your team or yourself).



## Dynamic typing
```javascript
var foo = 42;    // foo is now a Number
var foo = "bar"; // foo is now a String
var foo = true;  // foo is now a Boolean
```
## Data types
* Six data types that are primitives:
  * Boolean
  * Null
  * Undefined
  * Number
  * String
  * Symbol (new in ECMAScript 6)
* and Object

All types except objects define immutable values (values, which are incapable of being changed).

### Boolean type

Boolean represents a logical entity and can have two values: true, and false.

### Null type

The Null type has exactly one value: null. See null and Null for more details.

### Undefined type

A variable that has not been assigned a value has the value undefined. See undefined and Undefined for more details.

## Null vs Undefined
Null is a value that indicates a deliberate non-value(**only accessible through the null keyword**)

_Undefined_ is a value of type _undefined_ that indicates an uninitialized value — that is a value hasn't even been assigned yet. In Javascript it is possible to declare a variable without assigning a value to it. By default the variable's type is _undefined_. _undefined_ is a constant

```javascript
null === undefined // false
null == undefined // true
null === null // true

var TestVar = null;
alert(TestVar); //shows null
alert(typeof TestVar); //shows object

var TestVar;
alert(TestVar); //shows undefined
alert(typeof TestVar); //shows undefined

null = 'value' // ReferenceError
 undefined = 'value' // 'value'
```

## Inner function
**A function within another function**
Nested functions in JavaScript is that they can access variables in their parent function's scope

```javascript
function betterExampleNeeded() {
  var a = 1;
  function oneMoreThanA() {
    return a + 1;
  }
  return oneMoreThanA();
}
```

## Closures
```javascript
function makeAdder(a) {
  return function(b) {
    return a + b;
  };
}
var x = makeAdder(5);
var y = makeAdder(20);
x(6); // 6+5 = 11
y(7); // 20+7 = 27
```
