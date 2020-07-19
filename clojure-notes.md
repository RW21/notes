<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [-](#-)
- [Data structures](#data-structures)
    - [Maps](#maps)
    - [Keywords](#keywords)
    - [Sets](#sets)
        - [Hash sets](#hash-sets)
        - [Lists](#lists)
    - [Functions](#functions)
        - [Defining functions](#defining-functions)
        - [Destructuring](#destructuring)
    - [Anonymous Functions](#anonymous-functions)
    - [Iterations](#iterations)

<!-- markdown-toc end -->

## Control flow

- `if`
- `when`
  - Doesn't need else.
  
- `nil?`

## Data structures

- `[]` vectors

### Maps

- `{}`

```clojure
{:first-name "Charlie"
:last-name "Who"}

(hash-map :a 1 :b 2)

(get {:a 1} :a)
```

- `get` to retrieve.
- `get-in` to retrieve in nested.

### Keywords

`:34`, `:rumple`

- Keywords can be used as a function for lookup.

### Sets

#### Hash sets

- Same as sets in Python.
- `#{}`

### Lists

- `conj` to add to beginning of a list.

## Functions

### Defining functions

```clojure
(defn hello
	[first last]
	(str "hello" first last))
```

Arity overloading:

```clojure
(defn multi-arity
  ;; 3-arity arguments and body
  ([first-arg second-arg third-arg]
     (do-things first-arg second-arg third-arg))
  ;; 2-arity arguments and body
  ([first-arg second-arg]
     (do-things first-arg second-arg))
  ;; 1-arity arguments and body
  ([first-arg]
     (do-things first-arg)))
```

Something like `*args`

```clojure
(defn codger
   [& whippersnappers]
  (map codger-communication whippersnappers))
```

### Multifunctions

- `defmulti` and `defmethod`.

### Pre and post condition

- `:pre` and `:post`


### Apply

```clojure
(apply the-function args) ; (the-function args0 args1 args2 ...)
```

### Destructuring

```clojure
(defn my-first
   [[first-thing]]
   first-thing)

; returns first in a collection
```

```clojure
(defn announce-location
   [{lat :lat lng :lng}]
   (println (str "Treasure lat:" kat))
)
```

## Anonymous Functions

```clojure
(fn [param-list]
   function body)
   
; reader macros
(map #(str "Hi, " %)
   '("Hi" "sdasda"))
   
(* 8 3)
#(* % 3)

(#(str %1 " and " %2) "corn" "bread")
```

## Iterations

```clojure
(loop [iteration 0]
  (println (str "Iteration " iteration))
    (if (> iteration 3)
	    (println "Goodbye!")
		    (recur (inc iteration))))
			
```

- `loop` has better performace than recursion.
- `recur` knows how to take advantage of being the last expression in a function to avoid accumalating stack frames.

## Regular expressions

```clojure
#"regular-expressoin"
```


## Namespaces

- `def` def binds symbol to ithe value.
- `defn` is mashup of def and fn.
- `'symbol`

- Namespaces are a big lookup tables of vars.
- `ns` to switch and create namespaces.
- `namespace/function` to call from another ns.
- `require` to load a namespace.
- Namespace and filename must match.

```clojure
(ns blottsbooks.core
(:require blottsbooks.pricing)
(:gen-class))
```
