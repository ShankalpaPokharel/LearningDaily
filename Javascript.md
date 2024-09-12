# JavaScript Fundamental Part 1

<details>

<summary> <i>(datatype, operater, operator precedence, truthy and falsy, history, type converstion and Coercion, control flow statements )</i> </summary>



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

## How JavaScript works behind the Scenes ? 
---

<details>
<summary>(<i>JS Engine, Stack , Heap, compilation, execution context, event loop, lexical scoping, scope, scope chain, Hoisting , this keyword, diff between function and method, Regular function vs Arrow Function , Primitives vs Reference Type</i>)</summary>




Javascript is a high-level prototype-based object-oriented multi-paradigm interpreted or just-in-time compiled dynamic single-threaded garbage-collected programming language with first-class functions and a non-blocking event loop concurrency

![alt text](<images/Screenshot 2024-08-13 at 1.14.19 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.15.07 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.16.02 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.17.44 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.19.22 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.21.11 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.22.14 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.24.58 PM.png>)

What is JavaScript Engine?
Program that executes javascript code
Example V8 google node,  every browser have own js engin 
![alt text](<images/Screenshot 2024-08-13 at 1.32.21 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.39.28 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 1.43.00 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 7.41.48 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 7.42.40 PM.png>)

### Exection Contexts and The Call Stack
---

(<i>
    How JavaScript Execute in Stack ?
    what is Execution Context?
</i>)

![alt text](<images/Screenshot 2024-08-13 at 7.48.16 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 7.57.39 PM.png>)
![alt text](<images/Screenshot 2024-08-13 at 8.03.53 PM.png>)
after return c second is poped off , disapper from callstack 
global is poped off only when when tab is closed or program is terminated, otherwise it always there. 

* **Scoping**: How our program's variables are `organized` and `accessed`. "Where do variables live?" or "Where can we access a certain variable, and where not?"

* **Lexical scoping**: Scoping is controlled by `placement` of functions and blocks in the code;
* **Scope:** Space or environment in which a certain variable is `declared` (variable environment in case of functions). There is `global` scope, `function` scope, and `block` scope;

* **Scope of a variable**: Region of our code where a certain variable can be `accessed`. 


### Scope and Scope Chain 
---
<i>(`scope` is the place in our code where variables are declared )</i>

[Why don't use var in modern js](https://medium.com/@darshanunadkat67/avoid-using-var-in-javascript-422394ed11a3#:~:text=Function%20Scoping%3A%20Variables%20declared%20with,hoisting%20and%20scope%2Drelated%20issues.)


![alt text](<images/Screenshot 2024-08-13 at 10.46.55 PM.png>)

![alt text](<images/Screenshot 2024-08-13 at 10.56.50 PM.png>)

![alt text](<images/Screenshot 2024-08-13 at 11.15.12 PM.png>)


**Summary**

* Scoping asks the question "Where do variables live?" or "Where can we access a certain variable, and where not?";
* There are 3 types of scope in JavaScript: the global scope, scopes defined by functions, and scopes defined by blocks;
* Only let and const variables are block-scoped. Variables declared with var end up in the closest function scope;
* In JavaScript, we have lexical scoping, so the rules of where we can access variables are based on exactly where in the code functions and blocks are written;
* Every scope always has access to all the variables from all its outer scopes. This is the scope chain!
* When a variable is not in the current scope, the engine looks up in the scope chain until it finds the variable it's looking for. This is called variable lookup;
* The scope chain is a one-way street: a scope will never, ever have access to the variables of an inner scope;
* The scope chain in a certain scope is equal to adding together all the variable environments of the all parent scopes;
* The scope chain has nothing to do with the order in which functions were called. It does not affect the scope chain at

### Hoisting in Javascript 
---

![alt text](<images/Screenshot 2024-08-14 at 8.28.19 AM.png>)

(<I> we can't use function expression before declare cause of hoisting</I>)



**The Temporal Dead Zone (TDZ)** is a behavior that arises due to the way `let` and `const` declarations are hoisted in JavaScript. It refers to the period between the start of a block scope and the point where a `let` or `const` variable is declared, during which the variable cannot be accessed.

In simpler terms, when you try to access a `let` or `const` variable before it is declared, you'll get a `ReferenceError` because the variable is in the Temporal Dead Zone, which means it is uninitialized and inaccessible.

**Example:**

```javascript
console.log(x); // ReferenceError: Cannot access 'x' before initialization
let x = 5;
```

The TDZ does not apply to variables declared with `var` or function declarations, as they are hoisted and initialized with `undefined` at the beginning of their respective scopes.

The TDZ is a mechanism introduced in ES6 to catch certain types of errors and prevent the use of uninitialized variables, which can lead to bugs in your code.

![alt text](<images/Screenshot 2024-08-14 at 8.33.23 AM.png>)

![alt text](<images/Screenshot 2024-08-14 at 8.55.53 AM.png>)

(<I>Var is created a property in  the window object of the browser not const and let.</I>)

![alt text](<images/Screenshot 2024-08-14 at 9.00.10 AM.png>)


### This Keyword
---
![alt text](<images/Screenshot 2024-08-14 at 9.10.49 AM.png>)
![alt text](<images/Screenshot 2024-08-14 at 9.14.18 AM.png>)
![alt text](<images/Screenshot 2024-08-14 at 9.18.32 AM.png>)


### Difference between function and method
---

The difference between a function and a method lies primarily in their context and usage:

####  Function
---

- **Definition**: A function is a block of code designed to perform a specific task. It is a standalone piece of code that can be called anywhere in the program.
- **Context**: Functions are not tied to any object or class. They exist independently and can be invoked on their own.
- **Example**:

  ```javascript
  function greet() {
      return "Hello, World!";
  }

  console.log(greet()); // Output: "Hello, World!"
  ```

#### Method
---

- **Definition**: A method is a function that is associated with an object or a class. It is defined within the context of a class or an object and is typically used to perform actions related to that object or class.
- **Context**: Methods are invoked on objects or instances of classes. They often operate on data that is stored within the object or class.
- **Example**:

  ```javascript
  const person = {
      name: "John",
      greet: function() {
          return "Hello, " + this.name + "!";
      }
  };

  console.log(person.greet()); // Output: "Hello, John!"
  ```

#### Key Differences
---

- **Scope**: 
  - A function is generally a standalone block of code.
  - A method is tied to an object or class.
  
- **Invocation**:
  - A function is called by its name directly.
  - A method is called on an object or class instance using dot notation (e.g., `object.method()`).
  
- **Access to `this`**:
  - Functions do not have access to the `this` keyword unless they are called as methods or with specific binding.
  - Methods have access to the `this` keyword, which typically refers to the object they belong to.



### Regular Functions vs Arrow Functions 
---

![alt text](<images/Screenshot 2024-08-14 at 9.38.33 AM.png>)
![alt text](<images/Screenshot 2024-08-14 at 9.39.07 AM.png>)
Argument
![alt text](<images/Screenshot 2024-08-14 at 9.42.35 AM.png>)


### Primitives Vs Objects (Primitive vs Reference Types)
---

![alt text](<images/Screenshot 2024-08-14 at 9.46.53 AM.png>)

![alt text](<images/Screenshot 2024-08-14 at 9.49.21 AM.png>)


**Stack**

- **Purpose**: The stack is used for storing primitive data types and function call information in a last-in, first-out (LIFO) order.
- **Characteristics**: It's fast, automatically managed, but has a fixed size. It's where variables like numbers and booleans are stored.

**Heap**

- **Purpose**: The heap is used for dynamic memory allocation, where objects, arrays, and functions are stored.
- **Characteristics**: It allows for flexible memory use, is managed by the garbage collector, and is slower to access compared to the stack.

![alt text](<images/Screenshot 2024-08-14 at 9.55.50 AM.png>)
(<i>const is immutable only in premetive data type</i>)
![alt text](<images/Screenshot 2024-08-14 at 9.59.07 AM.png>)
we can use deep copy and shallow copy, to avoid reference to memory address of heap  Spread operator `{ ...obj }`, `Object.assign({},origianalObject)`, `.slice()` for arrays. Deep Copy: `JSON.parse(JSON.stringify(obj))`, `structuredClone(obj)`, `_.cloneDeep() (Lodash)`, custom recursive function.



Can't completely change Const the object
```js
const sampleObject = {
    name: "John Doe",
    age: 30,
    city: "New York",
    hobbies: ["reading", "hiking", "coding"]
};

sampleObject.age = 31;
sampleObject = {
    name: "Jane Smith",
    age: 25,
    city: "London",
    hobbies: ["painting", "gardening", "traveling"]
};
TypeError: Assignment to constant variable.

```

Shallow copy only work in the first level 
![alt text](<images/Screenshot 2024-08-14 at 9.59.07 AM.png>)

</details>


# Data Structures Modern Operator

<details>

<summary><i>(Array and Object destructuring, spread operator, OR and And operator , for of Loop, optional chaining, set and map)</i></summary>


### Array and Object Destructuring
---

Destructuring allows you to extract values from arrays or properties from objects and assign them to variables.

#### Basic Assigning and Default Values

**Array Destructuring:**

```javascript
const arr = [1, 2, 3];
const [x, y, z] = arr; // x=1, y=2, z=3

// Assigning default values
const [a, b, c = 5] = [7, 8]; // a=7, b=8, c=5 (default)
```

**Object Destructuring:**

```javascript
let a = 111;
let b = 999;
const obj = { a: 23, b: 7, c: 14 };

// Destructuring with default values
({ a, b, c: d = 10 } = obj); // a=23, b=7, d=14 (c renamed to d)

// Why parentheses? 
// Without parentheses, the JavaScript interpreter will treat the code block as a statement (unexpected token error).
```

#### Nested Objects and Nested Arrays

You can destructure nested objects and arrays directly:

**Nested Object Destructuring:**

```javascript
const openingHours = {
  mon: { open: 8, close: 20 },
  fri: { open: 10, close: 22 },
};

const {
  fri: { open, close },
} = openingHours; // open=10, close=22
```

**Nested Array Destructuring:**

```javascript
const nestedArr = [1, [2, 3], 4];
const [i, [j, k]] = nestedArr; // i=1, j=2, k=3
```

### Spread Operator (...)

The spread operator allows you to expand an array or object into its individual elements or properties.

**Basic Usage:**

```javascript
const arr = [7, 8, 9];
const newArr = [1, 2, ...arr];
console.log(newArr); // [1, 2, 7, 8, 9]
```

#### Difference Between Spread Operator and Destructuring

- **Spread Operator**: Expands elements into individual values (useful for copying or combining arrays/objects).
- **Destructuring**: Extracts elements/properties from arrays/objects and assigns them to variables.

**Copying an Array:**

```javascript
const arrCopy = [...arr]; // Creates a shallow copy of arr
```

**Joining Two Arrays:**

```javascript
const anotherArr = [10, 11];
const combinedArr = [...arr, ...anotherArr];
console.log(combinedArr); // [7, 8, 9, 10, 11]
```

### Rest Pattern and Parameters

The rest pattern allows you to group the remaining elements into a new array or object. It is the opposite of the spread operator and must be the last element in the destructuring assignment.

**Rest Pattern in Arrays:**

```javascript
const [first, second, ...rest] = [1, 2, 3, 4, 5];
console.log(rest); // [3, 4, 5]
```

**Rest Pattern in Objects:**

```javascript
const { a, b, ...others } = { a: 1, b: 2, c: 3, d: 4 };
console.log(others); // { c: 3, d: 4 }
```

**Rest Parameters in Functions:**

```javascript
function add(...numbers) {
  return numbers.reduce((acc, curr) => acc + curr, 0);
}

console.log(add(2, 3, 4)); // 9
```

**Why only at the end?**  
The rest pattern must be at the end of the destructuring assignment because it collects all remaining elements. If placed anywhere else, it would not be clear which elements should be included in the rest group.

### JavaScript Concepts: Short-Circuiting, Nullish Coalescing, Logical Assignment, and More

---

#### **1. Short-Circuiting with `&&` and `||`**

Short-circuiting refers to the way logical operators `&&` (AND) and `||` (OR) evaluate expressions.

- **OR (`||`) Operator:**
  - Returns the first truthy value or the last value if all are falsy.
  - Example:
    ```javascript
    console.log(3 || 'Jonas'); // Output: 3 (first truthy)
    console.log('' || 'Jonas'); // Output: 'Jonas' (second value is truthy)
    console.log(undefined || null); // Output: null (both are falsy)
    console.log(undefined || 0 || '' || 'Hello' || 23); // Output: 'Hello' (first truthy)
    ```

- **AND (`&&`) Operator:**
  - Returns the first falsy value or the last value if all are truthy.
  - Example:
    ```javascript
    console.log(0 && 'Jonas'); // Output: 0 (first falsy)
    console.log(7 && 'Jonas'); // Output: 'Jonas' (last truthy)
    console.log('Hello' && 23 && null && 'jonas'); // Output: null (first falsy)
    ```

---

#### **2. Nullish Coalescing Operator (`??`)**

- The Nullish Coalescing Operator (`??`) returns the right-hand side value if the left-hand side is `null` or `undefined`, otherwise, it returns the left-hand side value. It doesn't consider `0` or `''` as nullish.
- Example:
  ```javascript
  const guest = 0;
  const guestCorrect = guest ?? 10;
  console.log(guestCorrect); // Output: 0 (because 0 is not nullish)
  ```

---

#### **3. Logical Assignment Operators**

Logical assignment operators combine logical operators (`||`, `&&`, `??`) with assignment (`=`) to simplify code.

- **OR Assignment (`||=`):**
  - Assigns a value if the current value is falsy.
  - Example:
    ```javascript
    const rest1 = { name: 'Capri', numGuests: 20 };
    const rest2 = { name: 'La Piazza' };
    
    rest1.numGuests ||= 10;
    rest2.numGuests ||= 10;
    
    console.log(rest1.numGuests); // Output: 20 (numGuests is truthy)
    console.log(rest2.numGuests); // Output: 10 (numGuests is undefined)
    ```

- **Nullish Assignment (`??=`):**
  - Assigns a value if the current value is `null` or `undefined`.
  - Example:
    ```javascript
    rest1.numGuests ??= 10;
    rest2.numGuests ??= 10;
    
    console.log(rest1.numGuests); // Output: 20
    console.log(rest2.numGuests); // Output: 10
    ```

- **AND Assignment (`&&=`):**
  - Assigns a value only if the current value is truthy.
  - Example:
    ```javascript
    rest1.owner &&= '<ANONYMOUS>';
    rest2.owner &&= '<ANONYMOUS>';
    
    console.log(rest1.owner); // Output: undefined (no owner property)
    console.log(rest2.owner); // Output: '<ANONYMOUS>'
    ```

---

#### **4. `for...of` Loop**

- The `for...of` loop iterates over iterable objects (like arrays) and can be used to access values and indexes.
- Example:
  ```javascript
  const menuBook = ['Pizza', 'Pasta', 'Risotto'];
  
  // Just values
  for (const item of menuBook) console.log(item); 
  // Output: Pizza, Pasta, Risotto
  
  // Entries (index and value)
  for (const [i, el] of menuBook.entries()) console.log(`${i + 1}: ${el}`);
  // Output: 1: Pizza, 2: Pasta, 3: Risotto
  ```

---

#### **5. Optional Chaining (`?.`)**

- Optional chaining allows you to safely access deeply nested properties that might not exist.
- Example:
  ```javascript
  const restaurant = {
    name: 'Italiano',
    openingHour: {
      mon: { open: 9, close: 22 },
      tue: { open: 10, close: 22 },
    },
  };

  // Without Optional Chaining
  if (restaurant.openingHour.mon) console.log(restaurant.openingHour.mon.open);

  // With Optional Chaining
  const days = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun'];
  for (const day of days) {
    const open = restaurant.openingHour[day]?.open ?? 'closed';
    console.log(`On ${day}, we open at ${open}`);
  }
  // Output: On mon, we open at 9
  // Output: On wed, we open at closed
  ```
  
---

### Set and Map

#### **Sets**
- **Definition**: A collection of unique values. 
- **When to Use**: Use a Set when order doesn't matter and you need to store unique values.
- **Key Features**:
  - Strings are iterable and can be used in Sets.
  - Duplicate values are automatically removed.
  - Operations: `.add()`, `.delete()`, `.has()`, `.size`.

**Example**:
```javascript
const ordersSet = new Set(['Pasta', 'Pizza', 'Pizza', 'Risotto', 'Pasta']);
console.log(ordersSet); // Set { 'Pasta', 'Pizza', 'Risotto' }

ordersSet.add('Garlic Bread');
ordersSet.delete('Pizza');
console.log(ordersSet); // Set { 'Pasta', 'Risotto', 'Garlic Bread' }

for (const order of ordersSet) console.log(order);
// Outputs: Pasta, Risotto, Garlic Bread

const staff = ['Waiter', 'Chef', 'Waiter', 'Manager', 'Chef'];
const staffUnique = [...new Set(staff)];
console.log(staffUnique); // ['Waiter', 'Chef', 'Manager']
```

**When to Use Arrays vs. Sets**:
- **Arrays**: Use when order matters, and duplicates are allowed.
- **Sets**: Use when you need unique values and order doesn’t matter.

---

#### **Maps**
- **Definition**: A collection of key-value pairs, where keys can be of any data type.
- **When to Use**: Prefer Maps when you need key-value pairs, especially when keys aren’t strings.
- **Key Features**:
  - Keys can be of any data type (e.g., strings, numbers, arrays).
  - Methods: `.set()`, `.get()`, `.size`.

**Example**:
```javascript
const rest = new Map();
rest.set('name', 'Classico Italiano')
    .set(1, 'Firenze, Italy')
    .set('categories', ['Italian', 'Pizzeria', 'Vegetarian'])
    .set('open', 11)
    .set('close', 23)
    .set(true, 'We are open :D')
    .set(false, 'We are closed :(');

console.log(rest.get('name')); // 'Classico Italiano'
console.log(rest.get(true)); // 'We are open :D'

const time = 21;
console.log(rest.get(time > rest.get('open') && time < rest.get('close'))); // 'We are open :D'

const arr = [1, 2];
rest.set(arr, 'Test');
console.log(rest.get(arr)); // 'Test'

// Using Maps for questions and answers
const question = new Map([
    ['question', 'What is the best programming language in the world?'],
    [1, 'C'],
    [2, 'Java'],
    [3, 'JavaScript'],
    ['correct', 3],
    [true, 'Correct 🎉'],
    [false, 'Try again!']
]);

for (const [key, value] of question) {
    if (typeof key === 'number') console.log(`Answer ${key}: ${value}`);
}
```

**When to Use Maps vs. Objects**:
- **Maps**: Use when you need keys of various data types or when you set keys dynamically.
- **Objects**: Use for fixed and string-only key-value pairs.
### Which data struture to use?

![alt text](<images/Screenshot 2024-08-26 at 8.25.19 AM.png>)

![alt text](<images/Screenshot 2024-08-26 at 8.28.42 AM.png>)

![alt text](<images/Screenshot 2024-08-26 at 8.59.39 AM.png>)

</details>

## Functions in JavaScript

<details>

<summary><i>(First-Class and Higher Order Function, Function acceping Callbacks & and Returing Function, Bind Method, IIFE(Immedite Invoked Function Expression))</i></summary>

#### **Function Default Parameters**
- **Default Parameters (ES6)**: You can set default values for function parameters directly in the function signature.
- **Backward Compatibility (ES5)**: Before ES6, default parameters were handled with `||` operators.

**Example**:
```javascript
const bookings = [];
const createBooking = function(flightNum, numPassengers = 1, price = 199) {
    // ES5 fallback
    // numPassengers = numPassengers || 1;
    // price = price || 199;
  
    const booking = {
        flightNum,
        numPassengers,
        price
    };
  
    console.log(booking);
    bookings.push(booking);
};

createBooking("LH123");           // {flightNum: "LH123", numPassengers: 1, price: 199}
createBooking("LH123", 2, 800);   // {flightNum: "LH123", numPassengers: 2, price: 800}
createBooking("LH123", undefined, 100); // {flightNum: "LH123", numPassengers: 1, price: 100}
```
- **Best Practices**: When a function has multiple optional parameters, it's often better to use an object as an argument to increase readability.

#### **Passing Arguments: Value vs. Reference**
- **Primitives (Value Types)**: When passing primitives (e.g., strings, numbers, booleans) to a function, the function receives a copy of the value. Changes inside the function don’t affect the original variable.
- **Objects (Reference Types)**: When passing objects to a function, the function receives a reference to the object, meaning changes inside the function will mutate the original object.

**Example**:
```javascript
const flight = 'LH234';
const jonas = {
    name: 'Jonas Schmedtmann',
    passport: 12123123
};

const checkIn = function(flightNum, passenger) {
    flightNum = 'LH999'; // This does not affect the original 'flight' variable
    passenger.name = "Mr. " + passenger.name; // This does affect the original 'jonas' object
  
    if (passenger.passport === 12123123) {
        console.log('Check in');
    } else {
        console.log('Wrong passport');
    }
};

checkIn(flight, jonas);
console.log(flight); // 'LH234' - remains unchanged
console.log(jonas);  // { name: 'Mr. Jonas Schmedtmann', passport: 12123123 } - 'name' is changed
```

**Key Takeaways**:
- **Primitive Types**: Immutable, passed by value.
- **Reference Types**: Mutable, passed by reference. Changes in the function reflect outside the function.

#### **Common Pitfalls**
- **Unintentional Mutation**: Be cautious when modifying objects inside functions. Use techniques like object spread (`{...obj}`) or `Object.assign()` to create shallow copies if you need to avoid altering the original object.
  
- **Undefined Parameters**: When skipping parameters, especially in functions with multiple defaults, use `undefined` to maintain the correct order, letting default values take effect.



### First-Class and Higher-Order Function
---
![alt text](<images/Screenshot 2024-08-29 at 7.41.50 AM.png>)

First class is just a feature programming language either has or does not have. All it means that all functions are values.  There is no frist class function in practice . It just a concept. Thare are however higher order functions in practice which are possible because the language supports first class functions. 

###  The `call` and `apply` Methods

#### **The `call` Method**
- **Purpose**: The `call` method allows you to explicitly set the `this` context for a function and immediately invoke it.
- **Usage**: Useful when you want to borrow a method from one object and use it on another.

**Example**:
```javascript
const lufthansa = {
  airline: 'Lufthansa',
  iataCode: 'LH',
  bookings: [],
  book(flightNum, name) {
    console.log(`${name} booked a seat on ${this.airline} flight ${this.iataCode}${flightNum}`);
    this.bookings.push({ flight: `${this.iataCode}${flightNum}`, name });
  },
};

lufthansa.book(239, 'Jonas Schmedtmann'); // Normal method call
lufthansa.book(635, 'John Smith');

const eurowings = {
  airline: 'Eurowings',
  iataCode: 'EW',
  bookings: [],
};

const book = lufthansa.book;

// Using `call` to set `this` to `eurowings`
book.call(eurowings, 23, 'Sarah Williams'); 
console.log(eurowings); // Sarah Williams booked on Eurowings

// Using `call` again with `lufthansa`
book.call(lufthansa, 239, 'Mary Cooper'); 
console.log(lufthansa); // Mary Cooper booked on Lufthansa

const swiss = {
  airline: 'Swiss Air Lines',
  iataCode: 'LX',
  bookings: [],
};

book.call(swiss, 583, 'Mary Cooper'); // Mary Cooper booked on Swiss
```

#### **The `apply` Method**
- **Purpose**: The `apply` method is similar to `call`, but it takes arguments as an array instead of listing them individually.
- **Usage**: Useful when arguments are already in an array or when working with functions that require an array of arguments.

**Example**:
```javascript
const flightData = [583, 'George Cooper'];
book.apply(swiss, flightData); // Using `apply` to set `this` and pass arguments as an array
console.log(swiss); // George Cooper booked on Swiss

// `call` with spread syntax does the same as `apply`
book.call(swiss, ...flightData); 
```

#### **Key Differences**
- **`call`**: Takes arguments one by one.
- **`apply`**: Takes arguments as an array.

**Best Practice**: With modern JavaScript (ES6+), the `apply` method is less common because you can achieve the same result with `call` and the spread syntax (`...`).

### Functions Accepting Callbacks & Returning Functions
---

- **Functions Accepting Callbacks**: A function can take another function as an argument (a callback) and execute it within the function. This is useful for asynchronous operations or custom behavior.

  **Example**:
  ```javascript
  const greet = name => console.log(`Hello, ${name}`);
  const processUserInput = (callback) => {
      const name = prompt('Please enter your name.');
      callback(name);
  };
  processUserInput(greet);
  ```

- **Functions Returning Functions**: A function can return another function, allowing for powerful patterns like function factories or closures.

  **Example**:
  ```javascript
  const createGreeting = greeting => name => console.log(`${greeting}, ${name}`);
  const greetHello = createGreeting('Hello');
  greetHello('Jonas');
  ```

**Key Takeaway**: 
- **Callbacks**: Enable flexible and reusable code by passing functions as arguments.
- **Returning Functions**: Allows creating customized functions or preserving data via closures.


###  The `bind` Method
---


#### **The `bind` Method**
- **Purpose**: The `bind` method creates a new function with a fixed `this` context and, optionally, predefined arguments. Unlike `call` and `apply`, `bind` doesn’t immediately invoke the function—it returns a new function instead.

**Example**:
```javascript
const bookEW = book.bind(eurowings);
const bookLH = book.bind(lufthansa);
const bookLX = book.bind(swiss);

bookEW(23, 'Steven Williams'); // Binds `this` to `eurowings` and books a flight

// Partial Application: Pre-setting arguments
const bookEW23 = book.bind(eurowings, 23); // Pre-sets flight number 23 for `eurowings`
bookEW23('Jonas Schmedtmann');
bookEW23('Martha Cooper');
```

#### **Using `bind` with Event Listeners**
- **Context Fixing**: `bind` is particularly useful in event listeners where the `this` context may change (e.g., pointing to the element triggering the event rather than the object).

**Example**:
```javascript
lufthansa.planes = 300;
lufthansa.buyPlane = function () {
  console.log(this); // Logs the `lufthansa` object

  this.planes++;
  console.log(this.planes); // Increases the plane count for `lufthansa`
};

document.querySelector('.buy').addEventListener('click', lufthansa.buyPlane.bind(lufthansa));
// Ensures `this` in `buyPlane` points to `lufthansa` instead of the button element
```

#### **Partial Application with `bind`**
- **Partial Application**: `bind` can also be used to create a new function with some arguments pre-set, simplifying repetitive tasks.

**Example**:
```javascript
const addTax = (rate, value) => value + value * rate;
console.log(addTax(0.1, 200)); // Standard function call

const addVAT = addTax.bind(null, 0.23); // Pre-sets the VAT rate to 23%
console.log(addVAT(100)); // Applies 23% VAT to 100
console.log(addVAT(23));  // Applies 23% VAT to 23

// Alternative using closures:
const addTaxRate = function(rate) {
  return function(value) {
    return value + value * rate;
  };
};
const addVAT2 = addTaxRate(0.23); // Creates a function that always applies 23% VAT
console.log(addVAT2(100)); // Applies 23% VAT to 100
console.log(addVAT2(23));  // Applies 23% VAT to 23
```

**Key Takeaways**:
- **`bind` for `this` Context**: Use `bind` to ensure the correct `this` context in functions, particularly in asynchronous operations or event handlers.
- **Partial Application**: `bind` can pre-set arguments for functions, making it useful for repetitive tasks or creating specific utility functions.


### Best Practice Summary:

- **`call`**: Use for immediate function invocation with a specific `this` and fixed arguments.
- **`apply`**: Use when arguments are in an array (or prefer `call` with the spread operator).
- **`bind`**: Use to create a new function with a bound `this` context, ideal for event handlers and partial application.

### IIFE (Immediately Invoked Function Expressions)
---

#### **IIFE Explained**
- **What It Is**: An IIFE is a function that is defined and immediately executed.
- **Syntax**: Wrap the function in parentheses and follow it with `()` to invoke it.

**Example**:
```javascript
(function () {
  console.log('This will never run again');
  const isPrivate = 23;
})();

// This will ALSO never run again (Arrow Function IIFE)
(() => console.log('This will ALSO never run again'))();
```

#### **Why Use IIFE?**
1. **Encapsulation**: Variables defined inside an IIFE are not accessible outside of it, creating a private scope. This helps avoid polluting the global namespace and prevents variable name conflicts.
   - **Example**: `const isPrivate = 23;` inside the IIFE is not accessible outside.
   - **Reason**: Encapsulation is crucial in large codebases to manage scope and prevent accidental interference with other parts of the code.

2. **Immediate Execution**: IIFEs are useful when you need a piece of code to run once, like initialization logic, without leaving any lingering variables or functions in the global scope.

#### **Block Scope vs. IIFE**
- **Block Scope**: Modern JavaScript (ES6+) allows for similar encapsulation using block scope with `let` or `const` inside curly braces `{}`. However, variables declared with `var` are not block-scoped and can still leak out of the block.
  
**Example**:
```javascript
{
  const isPrivate = 23;  // Block-scoped, not accessible outside
  var notPrivate = 46;   // Not block-scoped, accessible outside
}

// console.log(isPrivate); // Error: isPrivate is not defined
console.log(notPrivate);  // 46, `var` is function-scoped, not block-scoped
```

**Key Takeaway**: 
- **IIFE**: Use for immediate, one-time execution with encapsulated scope.
- **Block Scope**: Use for modern, clean encapsulation without requiring an IIFE, but remember `var` does not respect block scope.

</details>


## Closures 


![alt text](<images/Screenshot 2024-08-30 at 7.09.14 AM.png>)
![alt text](<images/Screenshot 2024-08-30 at 7.13.19 AM.png>)
VE-variable envroment
![alt text](<images/Screenshot 2024-08-30 at 7.16.13 AM.png>)


### Array Methods 
**Array Methods:** Methods are functions that are attached to objects. Since arrays are objects in JavaScript, they have access to various built-in methods for manipulating and interacting with array data.

| **Method**  | **Description**                                      | **Modifies Original Array** | **Example** |
|-------------|------------------------------------------------------|-----------------------------|-------------|
| **`slice`** | Extracts part of the array, returns a new array       | No                           | `arr.slice(1, 3)` ➔ `['b', 'c']` |
| **`splice`**| Removes/replaces elements from the array              | Yes                          | `arr.splice(2)` ➔ `['a', 'b']` |
| **`reverse`** | Reverses the array order                             | Yes                          | `arr.reverse()` ➔ `['e', 'd', 'c', 'b', 'a']` |
| **`concat`** | Merges arrays, returns a new array                    | No                           | `arr.concat(arr2)` ➔ `['a', 'b', 'c', 'd', 'e', 'j', 'i', 'h', 'g', 'f']` |
| **`join`**   | Joins array elements into a string                    | No                           | `arr.join('-')` ➔ `'a-b-c-d-e'` |
| **`at`**     | Returns the element at a specific index (supports negative indexing) | No              | `arr.at(-1)` ➔ `'e'` |

### Additional Notes
- **`slice`** is useful for creating shallow copies of arrays.
- **`splice`** is typically used to remove elements or replace elements within an array.
- **`reverse`** can be handy for reversing the order of elements, but be cautious as it mutates the original array.
- **`concat`** is a non-destructive way to combine arrays.
- **`join`** is often used to create strings from array elements, with a specified separator.
- **`at`** provides a cleaner way to access elements from the start or end of an array, compared to traditional methods.


### Array Methods: `for...of` vs `forEach`
---
#### Example Code:
```javascript
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

// Using for...of loop with array.entries()
for (const [i, movem] of movements.entries()) {
  console.log("for...of");
  if (movem > 0) {
    console.log(`You deposited ${movem}`);
  } else {
    console.log(`Movement ${i + 1}: You withdrew ${Math.abs(movem)}`);
  }
}

console.log("-----FOREACH-----");

// Using forEach method
movements.forEach(function(movem, index, array) {
  if (movem > 0) {
    console.log(`You deposited ${movem}`);
  } else {
    console.log(`Movement ${index + 1}: You withdrew ${Math.abs(movem)}`);
  }
});
```

#### Key Points:
- **`for...of` Loop**:
  - Iterates over array elements.
  - Use `.entries()` to access both the index and the value.
  - Suitable when manual control over iteration is needed.

- **`forEach` Method**:
  - Higher-order function that takes a callback.
  - Automatically provides the current element, index, and the entire array.
  - Processes each element in sequence.

### My Learning:
I've learned the importance of understanding different array methods like `.at()`, `.slice()`, and `.splice()`. The `.at()` method is handy for accessing elements with both positive and negative indices. The `.slice()` method is useful when I need a portion of the array without altering the original one, as it returns a new array. On the other hand, `.splice()` not only extracts a portion but also changes the original array by removing the extracted elements.

In terms of looping methods, `for...of` requires manual handling to access both the index and the item, especially when using `.entries()`. However, `forEach` simplifies things by automatically providing the current item, index, and the entire array. It's convenient when I need to perform an action on each array element without worrying about manual indexing.

