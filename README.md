# js_fundamentals
Learn Javascript

# Glossary

1. [Unicode symbols](#unicode-symbols)
2. [Comments](#comments)
3. [Literals](#literals)
4. [Identifiers](#identifiers)
5. [Reserved words](#reserved-words)
6. [Fundamental types](#fundamental-types)
7. [Number](#number)
8. [Infinite](#infinite)
9. [Infinite examples](#infinite-examples)
10. [Infinite pitfalls](#infinite-pitfalls)
2. [Variables](#Variables)
3. [Aggregate initialize variables](#aggregate-initialize-variables)
4. [Safety aggregate initialize variables](#aggregate-initialize-variables)
5. [Variables with floating point](#variables-with-floating-point)
5. [Char variable](#char-variable)
6. [Struct declaration](#struct-declaration)
7. [Struct initialization](#struct-intialization)
8. [Union](#union)
8. [Memory alignment](#memory-alignment)
   [Move semantics](#move-semantics)
6. [Type conversions](#type-conversions)
 - [Static cast](#static-cast)
 - [Dynamic cast](#dynamic-cast)
 - [Reinterpret cast](#reinterpret-cast)
 - [Const cast](#const-cast)
7. [Type declaration](#type-conversions)
8. [Condition statement](#condiion-statement)
9. [Arrays](#Arrays)
10. [Loops](#Loops)
10. [Classes](#Classes)
11. [Examples](#Examples)
12. [Condition variables](#Condition-variables)
13. [Priority constructor](#Priority-constructor)


### Unicode symbols
    This article should contain table of unicode symbols

### Comments
```js
// One line comments

/* There is another
comment
*/ // another one comment.

/*
* Several.
* line
comment.
*/

/*----------------------------------------------------------------
    Maybe good delimeter comments
*/
```

### Literals
```js
12            // Number
1.2           // float number
"hello world" // String
'Hi'          // String
true          // Boolean true value
false         // Boolean false value
/javascript/gi // Literal "regular expression" (for searching by template)
null          // null Object
{ x:1, y:2 }  // initializer of object
[1,2,3,4,5]   // initializer of array
```

### Identifiers
```js

```

### Reserved words
```js
break   delete  function    return  typeof
case    do  if  switch  var
catch   else    in  this    void
continue    false   instanceof   throw   while
debugger    finally new true    with
default for null    try
// ans some addition
class const enum export extends import super

// reserved words in strict mode
implements let private public yield
interface package protected static

// follow words can't use as name variables functions, parameters
arguments eval

// next word reserved from Java lang
abstract double goto native static
boolean enum implements package super
byte export import private synchronized
char extends int protected throws
class final interface public transient
const float long short volatile

// Global words defined in JavaScript
arguments encodeURI Infinity Number RegExp
Array encodeURIComponent isFinite Object String
Boolean Error isNaN parseFloat SyntaxError
Date eval JSON parseInt TypeError
decodeURI EvalError Math RangeError undefined
decodeURIComponent Function NaN ReferenceError URIError
```

## Fundamental Types
```js
console.log(typeof 42)        // Expected output: "number"
console.log(typeof 42.42)     // Expected output: "number"
console.log(typeof "blubber") // Expected output: "string"
console.log(typeof true)      // Expected output: "boolean"
console.log(typeof undeclaredVariable) // Expected output: "undefined"
console.log(typeof null)      // Expected output: "object" also named as null-object
console.log(typeof undefined) // Expected output: "undefined"
```

### Number
```js
console.log(typeof 42)        // Expected output: "number"
console.log(typeof NaN)       // Expected output: "number"

// float number
console.log(typeof 42.42)     // Expected output: "number"

// Infinity
console.log(type of Infinity) // Expected output: "number"
console.log(typeof -Infinity) // Expected output: "number"
```

### Infinite
```js
console.log(Number.MAX_VALUE)         // Expected output: 1.7976931348623157e+308
console.log(Number.MAX_SAFE_INTEGER)  // Expected output: 9007199254740991
console.log(Infinity)                 // Expected output: Infinity

console.log(1/0)                                 // Expected output: Infinity
console.log(Infinity > Number.MAX_SAFE_INTEGER)  // Expected output: true
console.log(Infinity > Number.MAX_VALUE)         // Expected output: true
console.log(Infinity + 1)                        // Expected output: Infinity
console.log(Infinity * 10)                       // Expected output: Infinity
console.log(Infinity + Infinity)                 // Expected output: Infinity

console.log(Infinity / Infinity)                 // Expected output: NaN
console.log(Infinity % 5)                        // Expected output: NaN

// Create Infynity in js
console.log(Infinity)                    // Expected output: Infinity
console.log(Number.POSITIVE_INFINITY)    // Expected output: Infinity
console.log(Number.NEGATIVE_INFINITY)    // Expected output: Infinity

// Create Infynity by bif calculation
console.log(Math.pow(2,1024))            // Expected output: Infinity
console.log(-1*Math.pow(2,1024))         // Expected output: -Infinity

// Infinity division
console.log(100/Infinity)                // Expected output: 0

// here is " - " is an minus operator of number so we will see -0 in result
console.log(100/-Infinity)               // Expected output: -0

// divide by NaN give us NaN
console.log(Infinity+NaN)   // Expected output: NaN
console.log(Infinity-NaN)   // Expected output: NaN
console.log(Infinity*NaN)   // Expected output: NaN
console.log(Infinity/NaN)   // Expected output: NaN
console.log(100/NaN)        // Expected output: NaN

// comparing Infiniry with -Infinity
console.log(Infinity > -Infinity)       // Expected output: true

// checking for infinity with ==
console.log(Infinity == 1/0)            // Expected output: true
console.log(Infinity == "Infinity")     // Expected output: true
console.log(Infinity == "1"/"0")        // Expected output: true
console.log(Infinity == "1/0")          // Expected output: false

// checking for infinity with ===
console.log(Infinity === 1/0)            // Expected output: true
console.log(Infinity === "Infinity")     // Expected output: false
console.log(Infinity === "1"/"0")        // Expected output: true
console.log(Infinity === "1/0")          // Expected output: false

// checking for infinity with Object.is()
console.log(Object.is(Infinity, 1/0))        // Expected output: true
console.log(Object.is(Infinity, "Infinity")) // Expected output: false

// checking isFinite()
console.log(isFinite("Infinity"))       // Expected output: false
console.log(isFinite("37"))             // Expected output: true

console.log(Number.isFinite("Infinity"))         // Expected output: false
console.log(Number.isFinite("37"))               // Expected output: false
console.log(Number.isFinite(Number("Infinity"))) // Expected output: false
console.log(Number.isFinite(Number("37")))       // Expected output: true
```

### Infinite examples
One use case where Infinity is put to practical use is finding the minimum value in an array
```js
function finMinEle(arr){
    let min = Infinity;
    for(const item of arr){
        min = Math.min(min, item);
    }
    return min;
}

findMinEle([10,8,1,220]); // Expected output: 1
```

Negative Infinity can be used to get the smallest value in a logic block.
```js
function checkSmallestNumber(smallNumber) {
  if (smallNumber === Number.NEGATIVE_INFINITY) {
    return smallNumber;
  }
  return smallNumber;
}

console.log(checkSmallestNumber(-Number.MAX_VALUE))  // Expected output: -1.7976931348623157e+308
console.log(checkSmallestNumber(-Infinity))          // Expected output: -Infinity
```

### Infinite pitfalls
It happens when we parseInt number from forms
```js
console.log(parseInt('23years'))            // Expected output: 23
console.log(parseInt('less than 23years'))  // Expected output: NaN
console.log(parseInt('Infinity'))           // Expected output: NaN
```

But if we use parseFloat
```js
console.log(parseFloat('Infinity'))        // Expected output: Infinity
```

Json serialization: JSON.stringify() method serializes an infinite number to null
```js
const item = {
    availability: Infinity
}
let stock = JSON.stringify(item)
console.log(stock)                // Expected output: {"availability": null}
```

Math metods
```js
console.log(2 * Number.MAX_VALUE) // Expected output: Infinity
console.log(Math.pow(10,1000))    // Expected output: Infinity
```
Math. max() and Math. min() are the two Math methods when invoked without arguments resulting in -Infinity and Infinity respectively.
```js
let empty = [];
console.log(Math.max(...empty))  // Expected output: -Infinity
console.log(Math.min(...empty))  // Expected output: Infinity
```

### tempalte
```js

```


```js
export const JsStory = () => html` JS Story `;
```

```js
export const JsStory = () => html` JS Story `;
```

```js story
export const JsStory = () => html` JS Story `;
```

```js preview-story
export const JsPreviewStory = () => html` JS Preview Story `;
```

```html story

  Hello world!
  Click me!

```

```html preview-story

  Hello world!
  Click me!

```


## Fundamental types
The actual fundamental types you can see in official documentation: https://en.cppreference.com/w/cpp/language/types
<br><br>

## Operator Precedence
| Priorory | Operator | Description | Associativity |
| ------ | ------ | ------ | ------ |
| 1 | :: | [Scope resolution](https://en.cppreference.com/w/cpp/language/identifiers#Qualified_identifiers) | Left-to-right -> |
| 2 | a++ a-- | [Suffix/postfix increment and decrement](https://en.cppreference.com/w/cpp/language/operator_incdec) | Left-to-right -> |
|   | type()  type{} | [Functional cast](https://en.cppreference.com/w/cpp/language/explicit_cast) | Left-to-right -> |
|   |  a() | [Function call](https://en.cppreference.com/w/cpp/language/operator_other#Built-in_function_call_operator)  | Left-to-right -> |
|   |  a[] | [Subscript](https://en.cppreference.com/w/cpp/language/operator_member_access#Built-in_subscript_operator) | Left-to-right -> |
|   |  .   -> | [Member access](https://en.cppreference.com/w/cpp/language/operator_member_access#Built-in_member_access_operators) | Left-to-right -> |
| 3 |  ++a --a  | [Prefix increment and decrement](https://en.cppreference.com/w/cpp/language/operator_incdec) | Right-to-left <- |
|   |  +a -a  | [Unary plus and minus](https://en.cppreference.com/w/cpp/language/operator_arithmetic#Unary_arithmetic_operators) | Right-to-left <- |
|   |  ! ~ | [Logical NOT](https://en.cppreference.com/w/cpp/language/operator_logical) and [bitwise NOT](https://en.cppreference.com/w/cpp/language/operator_arithmetic#Bitwise_logic_operators) | Right-to-left <- |
|   |  (type)  | [C-style cast](https://en.cppreference.com/w/cpp/language/explicit_cast) | Right-to-left <- |
|   |  *a  | [Indirection (dereference)](https://en.cppreference.com/w/cpp/language/operator_member_access#Built-in_indirection_operator) | Right-to-left <- |
|   |  &a  | [Address-of](https://en.cppreference.com/w/cpp/language/operator_member_access#Built-in_address-of_operator) | Right-to-left <- |
|   |  sizeof  | [Size-of](https://en.cppreference.com/w/cpp/language/sizeof) | Right-to-left <- |
|   |  co_await  | [await-expression ](https://en.cppreference.com/w/cpp/language/coroutines) | Right-to-left <- |
|   |  new   new[]  | [Dynamic memory allocation](https://en.cppreference.com/w/cpp/language/new) | Right-to-left <- |
|   |  delete delete[]  | [Dynamic memory deallocation](https://en.cppreference.com/w/cpp/language/delete) | Right-to-left <- |
| 4 |  .*   ->*  | [Pointer-to-member](https://en.cppreference.com/w/cpp/language/operator_member_access#Built-in_pointer-to-member_access_operators) | Left-to-right -> |
| 5 | a*b a/b a%b | [Multiplication, division, and remainder](https://en.cppreference.com/w/cpp/language/operator_arithmetic#Multiplicative_operators) | Left-to-right -> |
| 6 | a+b a-b | [Addition and subtraction](https://en.cppreference.com/w/cpp/language/operator_arithmetic#Additive_operators) | Left-to-right -> |
| 7 | << >> | [Bitwise left shift and right shift](https://en.cppreference.com/w/cpp/language/operator_arithmetic#Bitwise_shift_operators) | Left-to-right -> |
| 8 | <=> | [Three-way comparison operator ](https://en.cppreference.com/w/cpp/language/operator_comparison#Three-way_comparison)  <span style="color:green">(Since C++20)</span> | Left-to-right -> |
| 9 | < <= > >= | [	For relational operators < and ≤ and > and ≥ respectively](https://en.cppreference.com/w/cpp/language/operator_comparison) | Left-to-right -> |
| 10 | == != | [For equality and not equality operators](https://en.cppreference.com/w/cpp/language/operator_comparison) | Left-to-right -> |
| 11 | a&b | [Bitwise AND](https://en.cppreference.com/w/cpp/language/operator_arithmetic#Bitwise_logic_operators) | Left-to-right -> |
| 12 | ^ | [Bitwise XOR (exclusive or)](https://en.cppreference.com/w/cpp/language/operator_arithmetic#Bitwise_logic_operators) | Left-to-right -> |
| 13 | | | [Bitwise OR (inclusive or)](https://en.cppreference.com/w/cpp/language/operator_arithmetic#Bitwise_logic_operators) | Left-to-right -> |
| 14 | && | [Logical AND](https://en.cppreference.com/w/cpp/language/operator_logical) | Left-to-right -> |
| 15 | || | [Logical OR](https://en.cppreference.com/w/cpp/language/operator_logical) | Left-to-right -> |
| 16 | a?b:c | [Ternary conditional](https://en.cppreference.com/w/cpp/language/operator_other#Conditional_operator) | Right-to-left <- |
|  | throw | [	throw operator](https://en.cppreference.com/w/cpp/language/throw) | Right-to-left <- |
|  | co_yield | [yield-expression ](https://en.cppreference.com/w/cpp/language/coroutines) (C++20) | Right-to-left <- |
|  | = | [Direct assignment](https://en.cppreference.com/w/cpp/language/operator_assignment#Builtin_direct_assignment) (provided by default for C++ classes) | Right-to-left <- |
|  | += -= | [Compound assignment](https://en.cppreference.com/w/cpp/language/operator_assignment#Builtin_compound_assignment) by sum and difference | Right-to-left <- |
|  | *= /= %= | [Compound assignment](https://en.cppreference.com/w/cpp/language/operator_assignment#Builtin_compound_assignment) by product, quotient, and remainder | Right-to-left <- |
|  | <<= >>= | [Compound assignment](https://en.cppreference.com/w/cpp/language/operator_assignment#Builtin_compound_assignment) by bitwise left shift and right shift | Right-to-left <- |
|  | &= ^= |= | [Compound assignment](https://en.cppreference.com/w/cpp/language/operator_assignment#Builtin_compound_assignment) by bitwise AND, XOR, and OR | Right-to-left <- |
| 17 | , | [Comma](https://en.cppreference.com/w/cpp/language/operator_other#Built-in_comma_operator) | Left-toright -> |
