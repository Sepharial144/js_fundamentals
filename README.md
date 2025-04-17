# js_fundamentals
Learn Javascript

# Glossary

1. [Unicode symbols](#unicode-symbols)
2. [Comments](#comments)
3. [Literals](#literals)
1. [Fundamental types](#fundamental-types)
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
12 // Number
1.2 // Number
"hello world" // String
'Hi' // String
true // Boolean true value
false // Boolean false value
/javascript/gi // Literal "regular expression" (for searching by template)
null // null Object
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
