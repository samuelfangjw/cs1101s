# Elements of programming

## Primitive Values
* Numbers
  * `123` `-123` `123.456`
* Boolean
  * `true` `false`
* Strings (covered in future studios)

## Expressions
An expression is a unit of code that evaluates to a value. The simplest form of expressions are primitive expressions, which are unmodified primitive values.
```
123 // An example of a primitive expression
```

### Combinations
Expressions can be combined with other expressions to form compound expressions called combinations.

```
123 + 456 // An example of a combination
```

:::note
The convention of placing the operator between the operands is known as Infix Notation. The other two notations (not used in source) are Prefix Notation and Postfix Notation.
:::

## Statements
Expressions can be turned into statements by adding a semicolon. A program is a series/sequence of one or more statements, which is executed line by line by the interpreter.

```
123;
123 + 456; // Evaluates to 597
```

## Constant Declarations
Constant declarations allow us to assign a name to a value that we use in our programs.

```
const radius = 1.0;
const area = math_PI * radius * radius; // calculate area of circle with radius 1.0
```

Constant declarations are the simplest form of abstraction. Abstraction can be thought of as 'hiding' the small details so that we can focus on the larger details. In this case, we can use the constants radius and area without having to worry about what the values associated with them are.

:::note
`math_PI` is a pre-declared constant. In source, some constants and functions are pre-declared. You may use these names in your programs.
:::

## Function Declarations
Functions are another form of abstraction. Similar to constant declarations, we abstract away the details of how the function is implemented. Let's take a look at the `find_area` function, which takes in a radius and returns the area of a circle.

```
// Function Declaration
function find_area(radius) {
    return math_PI * radius * radius;
}

// Function Application
const area_of_circle = find_area(1.0); // find area of circle with radius 1.0
```

Similar to constant declarations, we are declaring a name, `find_area` and assigning a function to this name. 

The function takes in a **parameter** radius and returns the value of the expression `math_PI * radius * radius`.`find_area(1.0)` applies the function to the **argument** `1.0`.

:::important
Note the difference between *parameter* and *argument*. Parameters are names declared in a function declaration which arguments are values supplied as part of a function call.
:::

### Number of parameters
Functions can have zero, one, or many parameters.

```
// Function with no parameters
function get_time() {
    // returns the current time
}

// Function with two parameters
function gcd(x, y) {
    // returns the GCD of x and y;
}
```

We can apply these functions as follows

```
const current_time = get_time();
const common_denominator = gcd(5, 10);
```

## Conditional Expressions
Sometimes, we want to perform different actions depending on whether a certain condition is met. One way to do this is to use conditional expressions which have the following form:

`predicate ? consequent-expression: alternative-expression`

A *predicate* is an expression whose value is either `true` or `false`. If the predicate evaluates to `true`, the *consequent-expression* is evaluated, else the *alternative-expression* is evaluated.

```
const is_raining = true;
const price_of_umbrella = is_raining ? 10 : 5; // Evaluates to 10
```

In this example, since the predicate `is_raining` is `true`, the consequent-expression `10` is evaluated. The value of `price_of_umbrella` is `10`.

:::note
It is generally a bad practice to write conditional expressions of the form
`predicate ? true : false` since predicate already evaluates to either `true` or `false`.
:::

## Operators
* Binary Operators (2 operands)
  * Arithmetic
    * Addition `+`
    * Subtraction `-`
    * Multiplication `*`
    * Division `/`
    * Modulo `%`
  * Comparison
    * Identical to `===`
    * Not identical to `!==`
    * Greater than `>`
    * Greater than equal to `>=`
    * Less than `<`
    * Less than equal to `<=`
  * Logical
    * Conjunction (AND) `&&`
    * Disjunction (OR) `||`
* Unary Operator (one operand)
  * not `!`
  * negative `-`

### Modulo Operation
The modulo operation returns the remainder after one number is divided by another.

```
5 % 1 // Evaluates to 0;
5 % 2 // Evaluates to 1;
5 % 3 // Evaluates to 2;
5 % 4 // Evaluates to 1;
5 % 5 // Evaluates to 0;
```

:::important
We can check if a number is even using the modulo operation.

`const is_five_even = 5 % 2 === 0;` evaluates to false

`const is_four_even = 4 % 2 === 0;` evaluates to true
:::

### Logical Operations
The conjunction (AND) operator checks if two expressions are *both* true.
```
true && true; // Evaluates to true
true && false; // Evaluates to false
false && true; // Evaluates to false
false && false; // Evaluates to false
```

The disjunction (OR) operator checks if *either* expression is true.
```
true || true; // Evaluates to true
true || false; // Evaluates to true
false || true; // Evaluates to true
false || false; // Evaluates to false
```

:::important
`expression_1 && expression_2` is equivalent to `expression_1 ? expression_2 : false`. If *expression_1* is false, we do not have to evaluate *expression_2*.

`expression_1 || expression_2` is equivalent to `expression_1 ? true: expression_2`. If *expression_1* is true, we do not have to evaluate *expression_2*.
:::