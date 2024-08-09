


# JavaScript Basics

### **Alert Example**

```javascript
alert("Hello world");
```

### **JavaScript Overview**

JavaScript is a high-level, object-oriented, multi-paradigm programming language. It is used to instruct computers to perform tasks, allowing developers to focus on functionality without worrying about complex details like memory management.

### **Web Applications**

JavaScript can be used for web applications on web servers using Node.js.

### **ES6 and ECMAScript**

![alt text](<images/Screenshot 2024-08-07 at 7.23.43 AM.png>)

ECMAScript (ES6) introduces new features and improvements to the JavaScript language.

![alt text](<images/Screenshot 2024-08-07 at 7.28.45 AM.png>)

### **Script Tag**

Add the script at the end of the body tag:

```html
<script src="script.js"></script>
```

### **Variable Naming**

- Variable names cannot start with a number.
- Variable names can only contain letters, numbers, underscores (`_`), and dollar signs (`$`).
- Avoid using reserved keywords.
- Do not start variable names with uppercase letters, as these are generally used for object naming conventions.
- Write meaningful variable names.

### **Data Types**

**Primitive (7)**:
- `Number`
- `String`
- `Boolean`
- `Undefined` (value taken by a variable that is not defined; e.g., `let children;`)
- `Null` (intentionally empty value)
- `Symbol` (introduced in ES2015; unique and immutable; not commonly used)
- `BigInt` (introduced in ES2020; for larger integers than the `Number` type can hold)

JavaScript has dynamic typing, meaning the type is detected automatically at runtime based on the value.

### **Comments**

- Multi-line comment: `/* */`

### **Variables**

- `let`: For variables that need to be changed.
- `const`: For variables that cannot be changed once assigned and cannot be declared empty. 
  * **First priority is `const` for good practice.**

- `var`: Legacy keyword with function scope. Use `let` instead, which has block scope.

Avoid directly assigning values like `ab = "ab"; console.log(ab);` without proper context or practices.

### **Operators**

#### **Assignment Operators**
- `=`: Assign
- `+`: Concatenate
- `+=`: Add and assign
- `*=`: Multiply and assign
- `x++`: Increment `x` by 1
- `x--`: Decrement `x` by 1

#### **Comparison Operators**
- `>`, `<`, `>=`, `<=`: Output in boolean

### **Operator Precedence**

Operator precedence determines the order in which operators are evaluated.

- **Comma**: `,`
- **Assignment, miscellaneous**: `=`, `+=`, `-=`, `*=`, `/=`, `%=` (assignment operators)
- **Conditional (ternary)**: `? :`
- **Logical OR**: `||`
- **Logical AND**: `&&`
- **Bitwise OR**: `|`
- **Bitwise XOR**: `^`
- **Bitwise AND**: `&`
- **Equality**: `==`, `!=`, `===`, `!==`
- **Relational**: `<`, `<=`, `>`, `>=`, `in`, `instanceof`
- **Shift**: `<<`, `>>`, `>>>`
- **Addition and subtraction**: `+`, `-`
- **Multiplication, division, and remainder**: `*`, `/`, `%`
- **Exponentiation**: `**`
- **Unary plus, unary negation, logical NOT, bitwise NOT, typeof, void, delete, await**: `+`, `-`, `!`, `~`, `typeof`, `void`, `delete`, `await`
- **Increment and decrement**: `++`, `--`
- **Unary negation and plus**: `-`, `+`
- **Grouping**: `(...)`
- **Member access**: `.`
- **Function call**: `()`
- **Optional chaining**: `?.`
- **Array subscript**: `[]`
- **New (with arguments)**: `new ...(...)`
- **New (without arguments)**: `new ...`



**Template Literals**: Allows you to directly embed variables, perform calculations, and write multiline strings easily.

```js
const jonas = `I'm ${firstName}, a ${year - birthYear} year old ${job}`;
```

* **Another name for `if else` is `control structure`.**

### **Type Conversion and Coercion**
---
**Type Conversion**: Manually converting a value from one type to another.

Example:
```js
const age = "12";
console.log(Number(age)); // Returns the Number type of 'age'
```

Note: `Number` doesn't change the original value of `age`, it just returns the converted value.

```js
console.log(Number('Jonas')); // Returns NaN
console.log(typeof NaN); // Returns 'number'
console.log(String(23)); // Converts the number 23 to a string
```

The reason `typeof NaN` returns `number` in JavaScript is because `NaN` (Not-a-Number) is a **special numeric value that represents an invalid or undefined result of a mathematical operation**.

**Type Coercion**: The automatic or implicit conversion of values from one data type to another by JavaScript. It can occur in various situations, such as in comparisons, arithmetic operations, or when manipulating values of different types.

Examples:
```js
2 + 3 + 4 + '5'; // Returns '95' (number + string concatenation)
'10' - '4' - '3' - 2 + '5'; // Returns '15' (string - number operations followed by string concatenation)
```

### Truthy and Falsy Values
---

In JavaScript, truthy and falsy values are used to determine the boolean value of an expression or value in a conditional context, such as in an `if` statement or a ternary operator.

**Falsy Values**:
A falsy value is a value that is considered `false` when evaluated in a boolean context. The following values are considered falsy in JavaScript:
- `0`
- `''` (empty string)
- `undefined`
- `null`
- `NaN`
- `false`

**Truthy Values**:
Any value that is not falsy is considered truthy, meaning it evaluates to `true` in a boolean context.

### Equality Operators: `==` vs `===`
---

- `===`: Strict equality operator, which doesn't perform type coercion. Always try to use this one.
- `==`: Loose equality operator that does perform type coercion.



### Boolean Logic
---
![alt text](<images/Screenshot 2024-08-08 at 11.54.35 PM.png>)

