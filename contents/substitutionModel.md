# Substitution Model

The substitution model is model to help us reason about programs in Source 1 and 2.

In the substitution model, we step through the program line by line and substitute name occurances with their values before evaluating the resulting expressions.

```js
const x = 1;

x + 1;
```

The substitution model for the above would be as follows:

- `const x`{.js} is evaluated and substituted into the rest of the block.

  ```js{highlight-lines="1,3[0:1]"}
  const x = 1;

  1 + 1;
  ```

  We are left with the following:

  ```js{start-from=3}
  1 + 1;
  ```

- Evaluate resulting expression

  ```js{start-from=3 highlight-lines="3[0:1]"}
  2;
  ```

<panel header="More about the substitution model">
  The substitution model gives us a simple way to reason about programs at a high level of abstraction. Like other oversimplified models, certain assumptions have to hold for the model to work. In future studios, we will explore how the model breaks down once we start to question these assumptions.<br><br>

  <box header="Challenge!">
    If you are familiar with other programming languages, try using the substitution model to evaluate some simple programs! Can you figure out how the substitution model breaks down?
  </box>
</panel>

## Function Application

There are two ways to evaluate function applications, _Applicative Order Reduction_ and _Normal Order Reduction_.

```js
function add_one(x) {
  return x + 1;
}

add_one(1 + 1);
```

We shall use the `add_one`{.js} function above in the sections below.

### Applicative Order Reduction

In Applicative Order Reduction, we evaluate the arguments before applying the function.

The above function will be evaluated as follows:

- Function `add_one`{.js} is declared.

  ```js{highlight-lines="1[0:]-3[:1]"}
  function add_one(x) {
    return x + 1;
  }

  add_one(1 + 1);
  ```

  We are left with

  ```js{start-from=5}
  add_one(1 + 1);
  ```

- The arguments are **evaluated first**. `1 + 1`{.js} is evaluated to the number `2`{.js}.

  ```js{start-from=5 highlight-lines="5[8:9]"}
  add_one(2);
  ```

- Apply the function by substitute parameters in the function body with the supplied arguments.

  ```{start-from=2 highlight-lines="2[0:1]"}
  2 + 1;
  ```

  We can evaluate the resulting expression to get `3`{.js}.

### Normal Order Reduction

In Normal Order Reduction, we substitute parameters with arguments (without evaluating the arguments) and only evaluate when expressions involving only primitive operators are obtained.

The above function will be evaluated as follows:

- Function `add_one`{.js} is declared.

- Substitute parameters with arguments first. In this case, `x`{.js} is substituted by `1 + 1`{.js}.

  ```{start-from=2 highlight-lines="2[0:6]"}
  (1 + 1) + 1;
  ```

- Only evaluate when an expression involving only primitive operators is obtained. We have already obtained a primitive expression (all operands are primitive values).

  ```{start-from=2 highlight-lines="2[0:1]"}
  2 + 1;
  ```

  ```{start-from=2 highlight-lines="2[0:1]"}
  3;
  ```

### Applicative Order vs Normal Order reduction

The difference lies in when we start evaluating the expressions! In layman's terms, for applicative order we simplify as much as possible before substituting names with their values whereas for normal order reduction we substitute before simplifying.

<box type="info">

**Applicative order reduction** is used in Source and most other popular programming languages. Despite the name, normal order reduction is less frequently used.
</box>

<box type="important">
Note that the output of programs evaluated using applicative order and normal order reduction may not necessarily be the same.
</box>

### Stepper tool

The stepper tool in the [Source Academy Playground](https://sourceacademy.org/playground) can help you better visualize the substitution model. Simply click on the stepper icon in the side panel and run a program (in Source 1 or Source 2 mode).
