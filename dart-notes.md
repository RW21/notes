<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [-](#-)
- [Types/Data structure](#typesdata-structure)
    - [List](#list)
    - [Map](#map)
    - [Functions](#functions)
        - [Parameter passing](#parameter-passing)
    - [Control flow](#control-flow)
    - [Objects](#objects)
        - [Classes](#classes)
        - [Generics](#generics)

<!-- markdown-toc end -->

## Basics

- `main()` function.
- `var` a way to declare without specifying types.
- If it starts with `_`, its private.

- `final`, `const`

## Types/Data structure

- Generic types
  - `List<int>`, `List<dynamic>`
- Use `var ` for local variables.

### List

```dart
var list = [1, 2, 3];
assert(list.length == 3);

var list = [0, ...list];

var nav = [
  'Home',
    'Furniture',
	  'Plants',
	    if (promoActive) 'Outlet'
		];
		
var listOfInts = [1, 2, 3];
var listOfStrings = [
  '#0',
    for (var i in listOfInts) '#$i'
	];
	
### Set

```dart
var halogens = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'};
var names = <String>{};

// true
halogens.contains('chlorine');
```

### Map

```dart
var gifts = {
  // Key:    Value
    'first': 'partridge',
	  'second': 'turtledoves',
	    'fifth': 'golden rings'
		};

var nobleGases = {
	2: 'helium',
	10: 'neon',
		18: 'argon',
		};
			  
```

## Functions

- Functions are first class objects!

```dart
bool isNoble(int atomicNumber) {
  return _nobleGases[atomicNumber] != null;
  }
  
// or

bool isNoble(int atomicNumber) => _nobleGases[atomicNumber] != null;

```

- `=>` is the shorthand syntax for `{return expr;}`.

### Parameter passing

```dart
// Named parameter
enableFlags(bold: true, hidden: false);

// Optional positional parameter
String say(String from, String msg, [String device]) {
  var result = '$from says $msg';
    if (device != null) {
	    result = '$result with a $device';
		  }
		    return result;
			}
			
```

## Control flow

```dart
if (isRaining()) {
  you.bringRainCoat();
  } else if (isSnowing()) {
    you.wearJacket();
	} else {
	  car.putTopDown();
	  }

var message = StringBuffer('Dart is fun');
for (var i = 0; i < 5; i++) {
  message.write('!');
  }
  
var collection = [0, 1, 2];
for (var x in collection) {
  print(x); // 0 1 2
  }
  
```

## Objects

### Classes

```dart
var p1 = new Point(2, 2);
var p2 = new Point.fromJson({'x': 1, 'y': 2});

class Point {
  double x;
    double y;
	}
	
void main() {
  var point = Point();
  point.x = 4; // Use the setter method for x.
  assert(point.x == 4); // Use the getter method for x.
  assert(point.y == null); // Values default to null.
		}
		
// Easy constructor
class Point {
  double x, y;
  
    // Syntactic sugar for setting x and y
	  // before the constructor body runs.
	    Point(this.x, this.y);
		}
```

- For getters and setters use `get` and `set`.

### Generics

