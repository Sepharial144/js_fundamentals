# js_fundamentals
Learn Javascript

# Glossary

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

## Boolean variables
There is a boolean initialization by assigning
```cpp
    bool isFalse = false;
    bool isTrue  = true;
```
There is a boolean initialization by aggregation
```cpp
    bool isFalse{false};
    bool isTrue{true};
```
<br><br>

## Numeric variables
Declare variables and intialization variables
So all of this variables in list are SIGNED

```cpp
    int8_t  a = 8;       // init int8_t variable
    int16_t b = -16;     // init int16_t variable
    int32_t c = -32;     // init int32_t variable
    int64_t d = -64;     // init int64_t variable

    uint16_t b = 16;     // init uint16_t variable
    uint32_t c = 32;     // init uint32_t variable
    uint64_t d = 64;     // init uint64_t variable

    float   f = 1.1f;    // init float variable
    double  d = 1.1f;    // init double variable
```
<br><br>

## Aggregate initialization variables
Aggregate initialize variables

```cpp
    int8_t  a{8};        // init int8_t variable
    int16_t b{-16};      // init int16_t variable
    int32_t c{-32};      // init int32_t variable
    int64_t d{-64};      // init int64_t variable

    // unsigned types
    int16_t b{16};       // init uint16_t variable
    int32_t c{32};       // init uint32_t variable
    int64_t d{64};       // init uint64_t variable

    float   f{1.1f};     // init float variable
    double  d{4.2f};     // init double variable

    // this variable will be initialized as 0
    int32_t zero_count{};

    // posible to create a variable like this
    int64_t addition_variable{ c + d }; 
    
    // follow variable won't exist and get compile error
    int64_t wont_exist{ not_exist1 + not_exist2 };   // compile error 
```
<br><br>

## Safety aggregate initialization variables
Some system has requirements for safety initialization, so it would be better to do like this:

```cpp
    // assignment      /  aggregation
    int8_t  a = 8;     //  int8_t  a{8};

    int16_t b = -16;    // int16_t b{16};
    int32_t c = -32;    // int32_t c{32};
    int64_t d = -64;    // int64_t d{64u};

    uint16_t b = 16;    // int16_t b{16};
    uint32_t c = 32;    // int32_t c{32};
    uint64_t d = 64u;   // int64_t d{64u};

    float   f = 1.1f;   // float   f{1.1f};
    double  d = 4.2f;   // double  d{4.2f};
```
<br><br>

## Variables with floating point
This article should have addition information anout numbers with floating point
This article should contain info from official documentation about setprecition
https://en.cppreference.com/w/cpp/io/manip/setprecision
```cpp
    float  f = 3.14159f;
    double d = 3.141592653589793239f;

    // so we can set precition of the printed result by command
    std::cout << std::setprecision(20); // set the precition of value
    std::cout << d << &std::endl; // 3.141592653589793239
```
<br><br>

## Char variable
```cpp
    char ch = '@';
    // or
    char ch{'@'};  
    // or
    char ch = 64; // the actual number of character in ASCII table
    // or
    char ch{64}; 
```
<br><br>

## Struct declaration
```cpp
    struct Person {
        std::string name;
        uint32_t age;
    };
```
<br><br>

## Struct initialization
```cpp
    struct Person {
        std::string name;
        uint32_t age;
    } person; // initialization person with empty properties

    //or with aggregate initialization
    Person marlin{"Marlin", 42};

    std::cout << "name: " << marlin.name << &std::endl;
    std::cout << " age: " << marlin.age << &std::endl;
```

## Union
```cpp
    // add an article with union and std::variant with difference
```
<br><br>

## Memory alignment
```cpp
    // declare without memory alignment
    struct Something {
        uint64_t value;
        uint64_t value2;
    };

    #pragma pack(push, 1) // declare macros which is alignment our structure
    struct Another {
        uint64_t value;
        uint64_t value2;
    };
    #pragma pack(pop) // endl of alignment memory structure

    int main(int argc, char* argv[]) {
        std::cout << "Size of Something: " << sizeof(Something) << &std::endl;  // shall be not 16 bytes
        std::cout << "Size of Another  : " << sizeof(Another) << &std::endl;    // this will show 16 bytes
        return 0;
    }
```
<br><br>

### Move semantics
```cpp
    // TODO: add move semantics exmplanation with example here, because it uses rvalue and lvaule meanings follow
```
<br><br>


## Type conversions
Convertion type in C style
```cpp
    char a = '@';
    int64_t b = (int64_t)a; // convert to int64_t as 64 number
```
<br>

## Static cast
> Two objects a and b are *pointer-interconvertible* if:<br>
>    - the are the same object<br>
>    - one is a union object and the other is a non-static data member of that object<br>
>    - one is a standard-layout class object and the other is the first non-static data member of that object or any base class subobject of that object<br>
>    - there exists an object c such that a and c are pointer-interconvertible, and c and b are pointer-interconvertible<br>

Convertion type in C++ style, static cast
```cpp
    char a = '@';
    int64_t b = static_cast<int64_t>(a); // convert to int64_t as 64 number
```
Exmaple 1: represent a cast from Base class to Derived 
```cpp
struct Base {};
struct Derived : Base { Base b; };
 
Derived d;
Base& base1 = d;
Base& base2 = d.b;

// this example represent downcast class from Derived to Base
static_cast<Derived&>(base1); // OK: lvalue denoting the original d object

// contain undefined behavior
static_cast<Derived&>(base2); // UB: the b subobject is not a base class subobject

// TODO: what about casting lvalue to rvalue?
```
Example 2: Interconvertible pointers<br>
```cpp
    union U { int32_t a; double b; } u;
    void* x = &u;                        // x's value is "pointer to u"
    double* y = static_cast<double*>(x); // y's value is "pointer to u.b"
    char* z = static_cast<char*>(x);     // z's value is "pointer to u"
```

Example 3: lvalue to rvalue conversion
```cpp
    std::vector<int32_t> v0{1,2,3};
    std::vector<int32_t> v2 = static_cast<std::vector<int32_t>&&>(v0);
    // after move, v0.size() = 0
```

Example 4: initializing conversion
```cpp
    int n = static_cast<int>(3.14); // n == 3
    std::vector<int32_t> v = static_cast<std::vector<int32_t>>(10); // v.size() == 10
```
Example 5: inverse of implicit conversion
```cpp
    int32_t n = static_cast<int>(3.14); // n == 3
    void* nv = &n;                    // convert to void ptr
    int32_t* ni = static_cast<int32_t*>(nv);  // from void ptr to int ptr
    // *ni == 3
```
Example 6: array-to-pointer followed by upcast
```cpp
    struct Base {};
    struct Derived : Base {};

    Derived a[10];
    [[maybe_unused]]
    Base* ptrBase = static_cast<Base*>(a);
    
    Base* ptrSame = static_cast<Base*>(a[0]); // the same as before

    // ptrBase and ptrSame point to the same address
    std::cout << (uint64_t)&(*ptrBase) << &std::endl;
    std::cout << (uint64_t)&(*ptrSame) << &std::endl;
```

Example 7: scoped enum to int32_t
```cpp
    enum class exEnum { ONE = 1, TWO, THREE }; // to move forward by the rule of enum TWO == 2, THREE == 3
    exEnum e = exEnum::TWO;
    int32_t two = static_cast<int>(e); // two == 2 == stEnum::TWO
```
Example 8: int32_t to enum, enum to another enum
```cpp
    enum class exEnum { ONE = 1, TWO, THREE };     // to move forward by the rule of enum TWO == 2, THREE == 3
    enum numericEnum { ONE = 1, TWO, THREE };      // 1,2,3
    exEnum e2 = static_cast<exEnum>(2);            // convert 2 to enum
    [[maybe_unused]]
    numericEnum eu = static_cast<numericEnum>(e2); // convert from enum class to enum
    static_cast<int32_t>(eu); // eu == 2
```

Example 9: pointer to member upcast      
```cpp
    struct Base { int32_t m = 42;};
    struct Derived {};

    Derived d;
    Base& br = d; //  upcast via implicit conversion

    int32_t Derived::*pm = &Derived::m;
    int32_t number = br.*static_cast<int Base::*>(pm); // need to clearify this moment
```  
Example 10: void* to any type
```cpp
    enum class exEnum { ONE = 1, TWO, THREE }; // to move forward by the rule of enum TWO == 2, THREE == 3
    exEnum e = exEnum::TWO;
    void* pVoid = &e;
    [[maybe_unused]]
    std::vector<int>* pV = static_cast<std::vector<int>*>(pVoid); // really? what's size of vector?
````
 > This example does#'t show actual size of the vector so maybe it is garbage.
<br>
<br>


## Dynamic cast
Dynamic cast convert
```cpp
// add actual dynamic casting
    char letter = '@';
    int64_t count = dynamic_cast(letter); // convert to int64_t as 64 number
```
<br>

## Reinterpret cast
Reinterpret cast convert the varaible in runtime
```cpp
    std::array<int32_t, 2> array{64, 64};
    int64_t res = reinterpret_cast<int64_t>(array.data()); // should return a number 5263992
```
***The following command migth not safe because undefined behavior***
<br>

## Const cast
Const cast convert
```cpp
    // TODO: add actual const cast casting with a lot of examples 
    std::array<uint64_t>(1) = {646464};
    int64_t b = std::reinterpret_cast<int64_t>(a); // convert to int64_t as 64 number
```
<br><br>

## Type declaration
```cpp
    typdef int MyIntType; // declare new type
    MyIntType variable = 42;
```


and one line condition
```cpp
    bool isTrue = true;
    std::string condition{};
    if (isTrue)  
        condition = "false"; // "true"
    else 
        condition = "true"; 
```


## Condition statement
```cpp
    bool isTrue = true;
    std::string condition{};
    if (isTrue) { 
        condition = "false"; // "true"
    } else { 
        condition = "true"; 
    }
```

## Ternary operators
```cpp
    bool isFalse = false;
    std::string res  = (isFalse == false)? "false": "true"; // "true"

    // add example with brances
```

## Operations wih bytes
```cpp
    /*
        This article should contain operation with bytyes
    */
```

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


##Enums
add the followwing examples with cast class enum to int and other 
https://en.cppreference.com/w/cpp/language/static_cast

## Arrays
Arrays
```cpp

```

## Loops
For loop
```cpp
    int8_t  a{8};        // init int8_t variable, the same as char
    int16_t b{16};       // init int16_t variable
    int32_t c{32};       // init int32_t variable
    int64_t d{64};       // init int64_t variable
    float   f{1.1f};     // init float variable
    double  d{1.1f};     // init double variable
```

### Classes

### Examples

### Condition variables

### Priority constructor
| Priorory | Consructor | rvalue | const rvalue | lvalue | const lvalue |
| ------ | ------ | ------ | ------ | ------ | ------ |
| 1 | T&& | yes | |  |  |
| 2 | const T&& | yes | yes | | |
| 3 | T& | | | yes | |
| 4 | const T& | yes | yes | yes | yes |
| 5 | T& | yes | | | |

https://habr.com/ru/articles/322132/

```sh
C++ code here
```
