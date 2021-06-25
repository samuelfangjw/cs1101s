# Elements of programming

## Primitive Values

The following are some examples of primitive values:

* Numbers
  * `123`{.js} `-123`{.js} `123.456`{.js}
* Boolean
  * `true`{.js} `false`{.js}
* Strings
  * `"String"`{.js}
* Null
  * `null`{.js}

<box type="info">
  Strings and Null are covered in later weeks.
</box>

## Expressions
An expression is a unit of code that evaluates to a value. The simplest form of expressions are primitive expressions, which are unmodified primitive values.

```js
123 // An example of a primitive expression
```

### Combinations
Expressions can be combined with other expressions to form compound expressions called combinations.

```js
123 + 456 // An example of a combination
```

<box type="info">
  The convention of placing the operator between the operands is known as Infix Notation. The other two notations (not used in source) are Prefix Notation and Postfix Notation.
</box>

## Statements
Expressions can be turned into statements by adding a semicolon. A program is a series/sequence of one or more statements, which is executed line by line by the source interpreter.

```js
123;
123 + 456; // Evaluates to 597
```

## Constant Declarations
Constant declarations allow us to assign a name to a value that we use in our programs.

```js
const radius = 1.0;
const area = math_PI * radius * radius; // calculate area of circle with radius 1.0
```

Constant declarations are the simplest form of abstraction. Abstraction can be thought of as 'hiding' the small details so that we can focus on the larger details. In this case, we can use the constants radius and area without having to worry about what the values associated with them are.

<box type="info">

  `math_PI`{.js} is a pre-declared constant. In source, some constants and functions are pre-declared. You may use these names in your programs without having to declare them first.
</box>

## Function Declarations
Functions are another form of abstraction. Similar to constant declarations, we abstract away the details of how the function is implemented. Let's take a look at the `find_area`{.js} function, which takes in a radius and returns the area of a circle.

```js
// Function Declaration
function find_area(radius) {
    return math_PI * radius * radius;
}

// Function Application
const area_of_circle = find_area(1.0); // find area of circle with radius 1.0
```

Similar to constant declarations, we are declaring a name, `find_area`{.js} and assigning a function to this name. 

The function takes in a **parameter** `radius`{.js} and returns the value of the expression `math_PI * radius * radius`{.js}.`find_area(1.0)`{.js} applies the function to the **argument** `1.0`{.js}.

<box type="important">

  Note the difference between **parameter** and **argument**. Parameters are names declared in a function declaration while arguments are values supplied as part of a function call.
</box>

<question type="mcq" header="Which of the following is correct?">

  ```js
    function magic(number) {
      return number + 1;
    }
    magic(1);
  ```
  <q-option correct>
      In the example above, <code>number</code> is the parameter and <code>1</code> is the argument.
    </q-option>
    <q-option reason="This is wrong. It should be the other way round.">
      In the example above, <code>1</code> is the parameter and <code>number</code> is the argument.
  </q-option>
</question>

### Number of parameters
Functions can have zero, one, or many parameters.

```js
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

```js
const current_time = get_time();
const common_denominator = gcd(5, 10);
```

## Conditional Expressions
Sometimes, we want to perform different actions depending on whether a certain condition is met. One way to do this is to use conditional expressions which have the following form:

`predicate ? consequent-expression : alternative-expression`{.js}

A *predicate* is an expression whose value is evaluated to either `true`{.js} or `false`{.js}. If the predicate evaluates to `true`{.js}, the *consequent-expression* is evaluated, else the *alternative-expression* is evaluated.

```
const is_raining = true;
const price_of_umbrella = is_raining ? 10 : 5; // Evaluates to 10
```

In this example, since the predicate `is_raining`{.js} is `true`{.js}, the consequent-expression `10`{.js} is evaluated. The value of `price_of_umbrella`{.js} is `10`{.js}.

<box type="info">

  It is generally a bad practice to write conditional expressions of the form `predicate ? true : false`{.js} since predicate already evaluates to either `true`{.js} or `false`{.js}.
</box>

<question type="mcq" header="What is the result after evaluating the following program?">

  ```js
    false ? 10 : 5;
  ```
  <q-option reason="Since the predicate evaluates to false, the result is the alternative-expression not the consequent-expression.">
      10
    </q-option>
    <q-option correct>
      5
  </q-option>
</question>

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

```js
5 % 1 // Evaluates to 0;
5 % 2 // Evaluates to 1;
5 % 3 // Evaluates to 2;
5 % 4 // Evaluates to 1;
5 % 5 // Evaluates to 0;
```

<box type="important">
One common use of the modulo operation is to check if a number is even or odd.

`const is_five_even = 5 % 2 === 0;`{.js} evaluates to `false`{.js}

`const is_four_even = 4 % 2 === 0;`{.js} evaluates to `true`{.js}
</box>

### Logical Operations
The conjunction (AND) operator checks if two expressions are *both* true.

```js
true && true; // Evaluates to true
true && false; // Evaluates to false
false && true; // Evaluates to false
false && false; // Evaluates to false
```

The disjunction (OR) operator checks if *either* expression is true.

```js
true || true; // Evaluates to true
true || false; // Evaluates to true
false || true; // Evaluates to true
false || false; // Evaluates to false
```

### Short circuit evaluation

`expression_1 && expression_2`{.js} is equivalent to `expression_1 ? expression_2 : false`{.js}. If `expression_1`{.js} is `false`{.js}, we do not evaluate `expression_2`{.js}.

Similarly, `expression_1 || expression_2`{.js} is equivalent to `expression_1 ? true: expression_2`{.js}. If `expression_1`{.js} is true, we do not evaluate `expression_2`{.js}.

<question type="checkbox" header="Which of the following values are displayed when the program below is evaluated?">

  ```js
    5 % 2 === 0 ? display(1) : display(2);
  ```

  **Note:** the `display` function displays the value passed in as argument.
  <q-option reason="`display(1)` is not evaluated.">
      1
    </q-option>
    <q-option correct>
      2
  </q-option>
</question>
