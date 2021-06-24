# JavaScript

## Course:  JavaScript Algorithms and Data Structures Certification

__NOTE__ from [freeCodeCamp](https://www.freecodecamp.org/)

### Comment Your JavaScript Code

* Comments are lines of code that JavaScript will intentionally ignore.
* Leave notes for yourself and others who are reading your code.
* To leave an in-line comment.
  * `// This is an in-line comment.`
* To leave a multi-line comment beginning with `/*` and ending iwth `*/`.

Here is an example:

  `/* This is a multi
  -line comment */`

### Declare JavaScript Variables

* __Data__ is anything that is meaningful to the computer.
    
    * undefined
    * null
    * boolean
    * string
    * symbol
    * bigint
    * number
    * object    
    
* Computer's need to be able to distinguish between numbers and strings, such as "12" and "123 dogs".  Whereas, "12" is a _number_, and "123 dogs" should be processed as a _string_.

* __Variables__ allow computers to store and manipulate data.
* Any of the above eight data types may be stored as a variable.
* Computer variables differ from mathematical variables in that they can store different values at different times.
* How do we declare variables?
    * By putting `var` in front of it.
    * Example: `var myName;`

* In JavaScript, we end statements with semicolons.

### Storing Values with the Assignment Operator

__Assignment Operator__ => `=`

  `myVariable = 5;`

* Assigns the _Number_ value `5` to `myVariable`.

* _Note_ => Any calculations to the right of the `=` operator are performed before variables to the left of the operator.

```js
var myVar;
myVar = 5;
```

### Assigning the Value of One Variable to Another

After a value is assigned to a variable using the _assignment operator_, you can assign the value of that variable to another variable using the assignment operator.

```javascript
var myVar;
myVar = 5;
var myNum;
myNum = myVar;
```

What is happening in the above example?

  * `myVar` is declared a variable with no value
  * `myVar` is assigned a value of 5
  * `myNum` is declared a variable with no value
  * `myNum` the contents of `myVar` (which is `5`) is assigned to the variable `myNum`
  * `myNum` has a value of `5`

Test Example:

```javascript
var a;
a = 7;
var = b;
b = a;
```

### Initializing Variables with the Assignment Operator

It is common to _initialize_ a variable to an initial value in the same line as it is declared.

```javascript
var myVar = 0;
```

What is happening in the above example?

* A new variable is created called `myVar`
* `myVar` is assigned a value of 5

### Understanding Uninitialized Variables

* When JavaScript variables are declared, they have an initial value of `undefined`
* If you do a mathematical operation on an `undefined` variable your result will be `NaN`, which means _"Not a Number_
* If you concatenate a string with an `undefined` variable, you will get a literal string of `undefined`
