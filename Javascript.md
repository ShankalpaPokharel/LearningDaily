# JavaScript Fundamental Part 1

<details>

<summary><i>(datatype, operater, operator precedence, truthy and falsy, history, type converstion and Coercion, control flow statements )</i></summary>



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

* **Everything we put in the () of an if statement is an expression which is evaluated as either `true` or `false`.** 


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


### Swith Statement 
---

more readable in some cases
```js
const day = "thursday";

switch(day){
    case 'monday':
        console.log("Plan course structure")
        console.log("go to coding meetup")
        break //if not break , it will continue to next break
    case 'tuesday':
        console.log("preapery theory video")
        break
    case 'tuesday':
        console.log("preapery theory video")
        break
    case 'wednesday':
    case 'thursday':
        console.log("react part")
        break
    case 'friday':
        console.log("record videos")
        break
    case 'saturday':
    case 'sunday':
        console.log("enjoy the weekend")
        break
    default:
        console.log("not a valid day")
}
```


### Statement and Expression
---
Expression : piece of code that produce the value
Statement : Bigger piece of code, doesn't produce value itself, perform some action complete code


### The conditional(Ternary) Operator
---
<i>(operator always produce value and its a expression)</i>

```js
const age = 23
age>= 18 ? console.log("I like to drink wine") : console.log("I like to drink water")

const drink = age >= 18 ? "wine" : "water"
console.log(drink)

console.log(`I like to drink ${age>=18 ? "wine" : "water"}`)
```
## A Brief History of Javascript

![alt text](<images/Screenshot 2024-08-09 at 9.05.47 AM.png>)

![alt text](<images/Screenshot 2024-08-09 at 9.10.29 AM Medium.jpeg>)

![alt text](<images/Screenshot 2024-08-09 at 9.14.35 AM.png>)

</details>

# JavaScript Fundamental Part 2

<details>

<summary><i>(function, array, object, destructuring, 4 Steps to Solve Any Problem and debugging )</i></summary>


**Strict Mode**:  
- Enables better error checking and avoids potential issues.

---

**3 Types of Functions**:

1. **Function Declaration**  
   - Can be called before it's defined.  
   - Example:  
     ```javascript
     function functionName() {
       // some action
     }
     ```

2. **Function Expression**  
   - Can't be called before it's defined.  
   - Example:  
     ```js
     const functionName = function(value) {
       // some action
     }
     const result = functionName(value);
     ```

3. **Arrow Function**  
   - Short, one-line function.  
   - Example:  
     ```javascript
     const calcAge = birthYear => 2037 - birthYear;
     const age = calcAge(1991);
     console.log(age);
     ```

![alt text](<images/Screenshot 2024-08-12 at 6.30.13 AM.png>)

---

**Destructuring**:  
- **Array**:  
  ```javascript
  const [val1, val2, val3] = [23, 432, 32];
  console.log(val1, val2, val3); // Output: 23, 432, 32
  ```

- **Object**:  
  ```javascript
  const { a, b } = obj;
  const { a: a1, b: b1 } = obj;
  const { a: a1 = aDefault, b = bDefault } = obj;
  const { a, b, ...rest } = obj;
  const { a: a1, b: b1, ...rest } = obj;
  const { [key]: a } = obj;
  ```

---

**Data Structures**:  

- **Array**:  
  ```javascript
  const friends = ['Michael', 'Steven', 'Peter', 'Jonas', 'Nick'];
  friends.push('Jay'); // Add to end
  friends.unshift('John'); // Add to start
  friends.pop(); // Remove from end
  friends.shift(); // Remove from start
  friends.splice(2, 1); // Remove 2nd element
  console.log(friends.indexOf('Steven'));
  console.log(friends.includes('Steven'));
  ```

- **Object**:  
  ```javascript
  const jonas = {
    firstName: 'Jonas',
    lastName: 'Schmedtmann',
    birthYear: 1991,
    job: 'teacher',
    friends: ['Michael', 'Steven', 'Peter'],
    hasDriversLicense: true,

    calcAge: function(birthYear) {
      return 2037 - birthYear;
    },

    getSummary: function() {
      return `${this.firstName} is a ${this.calcAge(this.birthYear)} year old ${this.job}, and he has ${this.hasDriversLicense ? 'a' : 'no'} driver's license.`;
    }
  };

  console.log(Object.keys(jonas));
  console.log(Object.values(jonas));
  console.log(jonas.calcAge(111));
  ```

- **Dot vs Bracket Notation**:  
  - Use dot notation for simple access:  
    ```javascript
    console.log(jonas.firstName);
    ```
  - Use bracket notation for dynamic access:  
    ```javascript
    const nameKey = 'Name';
    console.log(jonas['first' + nameKey]); // Output: Jonas
    ```

---


**4 Steps to Solve Any Problem**:

![alt text](<images/Screenshot 2024-08-12 at 8.28.47 PM.png>)

![alt text](<images/Screenshot 2024-08-12 at 8.24.59 PM.png>)
![alt text](<images/Screenshot 2024-08-12 at 8.26.30 PM.png>)
![alt text](<images/Screenshot 2024-08-12 at 8.27.44 PM.png>)
![alt text](<images/Screenshot 2024-08-12 at 8.28.20 PM.png>)

![alt text](<images/Screenshot 2024-08-12 at 8.45.56 PM.png>)

</details>