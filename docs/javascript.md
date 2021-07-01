# JavaScript

## Course:  JavaScript Algorithms and Data Structures Certification

__NOTE__ from [freeCodeCamp](https://www.freecodecamp.org/)

### Comment Your JavaScript Code

* Comments are lines of code that JavaScript will intentionally ignore.
* Leave notes for yourself and others who are reading your code.
* To leave an in-line comment.
  * `// This is an in-line comment.`
* To leave a multi-line comment beginning with `/*` and ending with `*/`.

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

### Understanding Case Sensitivity in Variables

* All variables and function names are case sensitive.
* `MYVAR`is not the same as `myVar` or `myvar`
* __Best Practice__ => Write variable names in JavaScript in _camelCase_.
* In _camelCase_, multi-word variable names have the first word in lowercase and the first letter of each subsequent word is capitalized.

What are some examples?

```javascript
var someVariable;
var anotherVariableName;
var thisVariableNameIsSoLong;
```

### Add Two Number with JavaScript

* `Number` is a data type in JavaScript which represents numeric data.
* JavaScript uses the `+` symbol as an addition operator when placed between two numbers.

What is an example?

`myVar = 5 + 10`

### Subtract One Number from Another with JavaScript

* You can also subtract one number from another.
* JavaScript uses the `-` symbol for subtraction.

What is an example?

`myVar = 16 - 6;`

### Multiply Two Numbers with JavaScript

* You can also multiply one number by another number.
* JavaScript uses the `*` symbol for multiplication of two numbers.

What is an example?

`myVar = 13 * 13`

### Divide One Number by Another with JavaScript

* You can also divide one number by another.
* JavaScript uses the `/` symbol for division.

What is an example?

`myVar = 16 / 2;`

### Increment a Number with JavaScript

* You can easily _increment_ or add one to a variable with a `++` operator.
* The above is equal to => `i = i + 1;`
* The entire line becomes `i++;`, eliminating the need for the equal sign.

What is an example?

```javascript
var myVar = 87;
// Only change code below this line
myVar = myVar + 1;
myVar++;
```

### Decrement a Number with JavaScript

* You can easily _decrement_ or decrease a variable by one with the `--` operator.
* Example => `i--;`
* The above is equal to => `i = i - 1;`
* The entire line becomes `i--;`, eliminating the need for the equal sign.

### Create Decimal Numbers with JavaScript

* We can store decimal numbers in variables too.
* Decimal numbers are sometime referred to as _floating point_ numbers or _floats_.
* Not all real numbers can accurately be represented in _floating point_, which can lead to rounding errors.

What is an example?

`var ourDecimal = 5.7;`

### Multiply Two Decimals with JavaScript

* In JavaScript, you can also perform calculations with decimal numbers.
* Let's multiply two decimals together.

What is an example?

`var product = 2.0 * 2.5;`

### Divide One Decimal by Another with JavaScript

What is an example?

`var quotient = 4.4 / 2.0;`

### Finding a Remainder in JavaScript

* The _remainder_ operator `%` gives the remainder of the division of two numbers.

Example

```javascript
5 % 2 = 1 because
Math.floor(5 / 2) = 2 (Quotient)
2 * 2 = 4
5 - 4 = 1 (Remainder)
```

Usage

* In mathematics, a number can be checked to be even or odd by checking the remainder of the division of the number by `2`.

```javascript
17 % 2 = 1 (17 is Odd)
48 % 2 = 0 (48 is Even)
```

__Note:__ The _remainder_ operator is sometimes incorrectly referred to as the modulus operator.  It is very similar to modulus, but does not work properly with negative numbers.

Test Example

```javascript
var remainder;
remainder = 11 % 3
```

### Compound Assignment with Augmented Addition

* In programming, it is common to use assignments to modify the contents of a variable.
* Remember that everything to the right of th equals sign is evaluated first, so we can say:
`my Var = myVar + 5;` to add `5` to `myVar`.
* Since this is such a common pattern, there are operators which do both - a mathematical operation and assignment in one step.
* One such operator is the `+=` operator.

What is an example?

```javascript
var myVar = 1; 
myVar += 5;
console.log(myVar);
```

Test Example

```javascript
a = a + 5;
b = b + 17;
c = c + 8;
```

Can Be:

```javascript
a += 5;
b += 17;
c += 8;
```

### Compound Assignment With Augmented Subtraction

* Like the `+=` operator, `-=` subtracts a number from a variable.

Example

`myVar = myVar -5;`

* will subtract `5` from `myVar`.  Can be rewritten as :

`myVar -= 5;`

Test Example:

```javascript
a = a - 6;
b = b - 15;
c = c - 1;
```

Can Be:

```javascript
a -= 6;
b -= 15;
c -= 1;
```

### Compound Assignment With Augmented Multiplication

* The `*=` operator multiplies a variable by a number.

`myVar = myVar * 5;`

* will multiply `myVar` by `5`.  This can be rewritten as:

`myVar *= 5;`

Test Example:

```javascript
var a = 5;
var b = 12;
var c = 4.6;

// Only change code below this line
a = a * 5;
b = 3 * b;
c = c * 10;
```

Can Be:

```javascript
a *= 5;
b *= 3; 
c *= 10;
```


### Compound Assignment With Augmented Division



