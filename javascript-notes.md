# Basics

## Functional

Composing pure functions, avoiding shared state, mutable data, and side-effects. FP is declarative rather than imperative, and application state flows through pure functions.

```javascript
script_a = {living : true}

["A", "B"].forEach(l => console.log(l));

filter(scripts, script => script.living)

map(rtlScripts, s => s.name)

// Parameters: combining function and a start value
reduce([1, 2, 3, 4], (a, b) => a + b, 0)
```

## String

- Template literals

```javascript
`half of 100 is ${100 / 2}`
```

## Program control

### if

```javascript
// One line if
if (a == 1) return 1
```

### loops

```javascript
["A", "B"].forEach(l => console.log(l));
```

## Logical operators

```javascript
console.log(null || "user")
// → user
console.log("Agnes" || "user")
// → Agnes
```

## Functions

- Javascript doesn't care much about number of arguments.

### Arrow operator

```javascript
const power = (base, exponent) => {
    if (exponent == 0) return 1 
    let result = base
    for (let i = 0; i < exponent - 1; i++) {
        result *= base
    }
    return result
}

const square = x => x * x;
```

### Closure

- Being able to reference a specific instance of a local binding in an enclosing scope—is called closure.

```javascript
function wrapValue(n) {
  let local = n;
  return () => local;
}

function multiplier(factor) {
   return number => number * factor;
}
let twice = multiplier(2); 
console.log(twice(5));
// → 10
```

### Rest parameter

```javascript
function max(...numbers) {
let result = -Infinity;
for (let number of numbers) {
     if (number > result) result = number;
   }
   return result;
 }
console.log(max(4, 1, 9, -2)); // → 9
```

### Binding

```javascript

function phi(table) {
return (table[3] * table[0] - table[2] * table[1]) /
Math.sqrt((table[2] + table[3]) * (table[0] + table[1]) * (table[1] + table[3]) * (table[0] + table[2]));
}

// Use bindings

function phi([n00, n01, n10, n11]) { return (n11 * n00 - n10 * n01) /
Math.sqrt((n10 + n11) * (n00 + n01) * (n01 + n11) * (n00 + n10));
}
```

## Data structures

Numbers, strings, and Booleans, are all immutable. Objects are mutable.

### Object

```javascript
let descriptions = {
x: 1,
"touched tree": "Touched a tree"
};

// Add key
descriptions.potato = 4

Object.keys(descriptions)

let objectA = {a: 1, b: 2};
Object.assign(objectA, {b: 3, c: 4});
console.log(objectA);
// → {a: 1, b: 3, c: 4}
```

### Strings

- `trim()`
- `indexOf()`
- `join()`
- `split()`

### Arrays

- `push()`

# Functional programming

Imperative programming is based on control flow. Declarative programming is a style of programming where the programmers tell the computer what to do by telling it what they want.

## Currying

```javascript
const add = x => (y) => x + y
// Rambda
// const add = curry((x, y) => x + y)
const add1 = add(1)

add1(3)
// 4
```

## Ramda

- `complement()`
- `both()`
- `either()`
- `pipe()`
  
### Functions

- `curry()`
- `flip()`
- Placeholder `__`
    - Only works for curried functions.

### Special placeholder

If g is a curried ternary function and _ is R.__, the following are equivalent:

```javascript
    g(1, 2, 3)
    g(_, 2, 3)(1)
    g(_, _, 3)(1)(2)
    g(_, _, 3)(1, 2)
    g(_, 2, _)(1, 3)
    g(_, 2)(1)(3)
    g(_, 2)(1, 3)
    g(_, 2)(_, 3)(1)
```
