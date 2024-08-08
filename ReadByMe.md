## Markdown Cheetsheet

<details>
<summary> Collapisable Section in Markdown</summary>

### Heading

1. Foo
2. Bar
    - Baz
    - Qux

### Some Javascript

```js
function logSomething(something) {
    console.log("Something", something);
}
```

</details>

<details>
<summary>Code / Markdown</summary>

````md
<details>
  <summary>Click me</summary>
  
  ### Heading
  1. Foo
  2. Bar
     * Baz
     * Qux

### Some Javascript

```js
function logSomething(something) {
    console.log("Something", something);
}
```

</details>
````

</details>

## Javascript

<details>

<summary> Async in JavaScript (bloking and non blocking code) </summary>
<br>
Asynchronous is a non-blocking architecture, so the execution of one task isn't dependent on another. Tasks can run simultaneously. Synchronous is a blocking architecture, so the execution of each operation depends on completing the one before it.

Execute context : execute one line of code at a time, each oreration waits for the last one to complete before executing

| Blocking Code                                 | Non Blocking Code                            |
| --------------------------------------------- | -------------------------------------------- |
| Block the flow of Program ---> Read File Sync | Doesn't block execution ---> Read File Async |

<b> Set timeout </b> : execute after given time
![alt text](<images/Screenshot 2024-07-25 at 12.47.05 PM.png>)

![alt text](<images/Screenshot 2024-07-25 at 1.59.43 PM.png>)

</details>

<details>
<summary><b>Event Loop</b></summary>
The event loop in JavaScript is a system that allows the language to handle multiple tasks, like fetching data or responding to user input, without blocking other code. Even though JavaScript runs on a single thread, the event loop helps manage tasks by executing them in the order they complete.

### Key Components:

-   **Call Stack**: Where functions are executed.
-   **Web APIs**: Browser features like `setTimeout` or `fetch` that handle tasks asynchronously.
-   **Callback Queue**: Holds completed tasks waiting to be executed.
-   **Event Loop**: Moves tasks from the callback queue to the call stack when it's empty.

</details>

<details>
<summary><b>Promise</b></summary>

## Promise

The `Promise` object represent the eventual completion (or failure) of an asynchronous operation and its resulting value.

A `Promise` is in one of these states:

-   **`pending`**: initial state, neither fulfilled nor rejected.
-   **`fulfilled`**: meaning that the operation was completed successfully.
-   **`rejected`**: meaning that the operation failed.

```js
const promiseFour = new Promise(function (resolve, reject) {
    setTimeout(function () {
        let error = true;
        if (!error) {
            resolve({ username: "John", password: "123" });
        } else {
            reject("ERROR: Something went wrong");
        }
    }, 1000);
});

promiseFour
    .then((user) => {
        console.log(user);
        return user.username;
    })
    .then((username) => {
        console.log(username);
    })
    .catch(function (error) {
        console.log(error);
    })
    .finally(() => console.log("The promise is either resolved or rejected"));

async function getAllUsers() {
    try {
        const response = await fetch("https://jsonplaceholder.typicode.com/users");

        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.log("E: ", error);
    }
}

getAllUsers();
```

### Promise using async await

async await handle resolve only. doesn't handle error or reject . To solve thtis problem use `try` and `catch`

```js
const promiseFive = new Promise(function (resolve, reject) {
    setTimeout(function () {
        let error = true;
        if (!error) {
            resolve({ username: "javascript", password: "123" });
        } else {
            reject("ERROR: JS went wrong");
        }
    }, 1000);
});

async function consumePromiseFive() {
    try {
        const response = await promiseFive;
        console.log(response);
    } catch (error) {
        console.log(error);
    }
}

consumePromiseFive();
```

</details>

<details>
<summary><b>Fetch</b></summary>

Note: The `promise` returned by `fetch()` will `reject` on some errors, such as a network error or a bad scheme. However, if the server responds with an `error` like `404`, then `fetch()` fulfills with a Response, so we have to check the status before we can read the response body.

The `Response.status` property tells us the numerical status code, and the `Response.ok` property returns true if the status is in the 200 range.

```js
// URL to which the request is sent
const url = "https://api.example.com/data";

// Request headers
const headers = {
    "Content-Type": "application/json",
    Authorization: "Bearer your_token_here",
};

// Request body data (in JSON format)
const requestData = {
    key1: "value1",
    key2: "value2",
};

// Fetch function with headers and POST request
fetch(url, {
    method: "POST", // HTTP method
    headers: headers, // Headers object
    body: JSON.stringify(requestData), // Convert requestData to JSON string
})
    .then((response) => {
        if (!response.ok) {
            throw new Error("Network response was not ok");
        }
        return response.json(); // Parse JSON data from response
    })
    .then((data) => {
        console.log("Success:", data);
    })
    .catch((error) => {
        console.error("Error:", error);
    });
```

![alt text](<images/Screenshot 2024-07-25 at 1.59.43 PM.png>)

</details>

<details>
<summary><b>Callback Function and Callback Hell</b></summary>

### Callback Function

A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of action. In JavaScript, callbacks are commonly used to handle asynchronous operations, like network requests or reading files.

#### Example of a Callback Function

Consider the `setTimeout` function, which executes a callback after a specified delay:

```javascript
function greet() {
    console.log("Hello, World!");
}

setTimeout(greet, 2000); // 'greet' is the callback function
```

### Callback Hell

Callback hell, also known as "Pyramid of Doom," refers to the situation in which callbacks are nested within each other, leading to code that is difficult to read, maintain, and debug. This often results in deeply indented and complex code structures.

#### Example

```javascript
login(user, function (err, userInfo) {
    if (err) {
        console.error(err);
    } else {
        fetchPosts(userInfo, function (err, posts) {
            if (err) {
                console.error(err);
            } else {
                fetchComments(posts, function (err, comments) {
                    if (err) {
                        console.error(err);
                    } else {
                        console.log("All comments:", comments);
                    }
                });
            }
        });
    }
});
```

### Solutions

#### Using Promises

```js
login(user)
    .then((userInfo) => fetchPosts(userInfo))
    .then((posts) => fetchComments(posts))
    .then((comments) => console.log("All comments:", comments))
    .catch((err) => console.error(err));
```

#### Using Async/Await

```js
async function processUser() {
    try {
        const userInfo = await login(user);
        const posts = await fetchPosts(userInfo);
        const comments = await fetchComments(posts);
        console.log("All comments:", comments);
    } catch (err) {
        console.error(err);
    }
}

processUser();
```

</details>

## React


<details>
<summary><b>`useMemo` and `useCallback`</b></summary>

Memoization is a specific form of optimization where the results of function calls are cached based on the input arguments. This means that when the same function is called with the same arguments, instead of recalculating the result, the stored (cached) result is returned.

## `useMemo` vs `useCallback` in React

In React, `useMemo` and `useCallback` are hooks that help optimize performance by memoizing values and functions. Here's a breakdown of the differences and when to use each:

### `useMemo`

-   **Purpose:** `useMemo` is used to memoize the result of a function call. It prevents expensive calculations from being re-executed on every render if the dependencies haven't changed.
-   **Usage:** It returns a memoized value.
-   **Syntax:**
    ```javascript
    const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
    ```
    Here, `computeExpensiveValue(a, b)` will only be recomputed if either `a` or `b` changes.

### `useCallback`

-   **Purpose:** `useCallback` is used to memoize a function itself. It prevents the function from being recreated on every render if the dependencies haven't changed. This is useful when passing callbacks to child components, as it prevents unnecessary re-renders.
-   **Usage:** It returns a memoized function.
-   **Syntax:**
    ```javascript
    const memoizedCallback = useCallback(() => {
        doSomething(a, b);
    }, [a, b]);
    ```
    The function `doSomething(a, b)` will only be recreated if either `a` or `b` changes.

### Key Differences

1. **Output:**

    - `useMemo` returns a memoized value.
    - `useCallback` returns a memoized function.

2. **Use Case:**
    - Use `useMemo` when you want to memoize the result of a computation to avoid recalculating it unnecessarily.
    - Use `useCallback` when you want to prevent function re-creation, especially when passing functions as props to child components that rely on reference equality to avoid re-renders.

### Example

```js
import React, { useMemo, useCallback } from "react";

function MyComponent({ list }) {
    // useMemo to memoize an expensive computation
    const sortedList = useMemo(() => {
        return list.sort((a, b) => a - b);
    }, [list]);

    // useCallback to memoize a function
    const handleClick = useCallback(() => {
        console.log("Clicked!");
    }, []);

    return (
        <div>
            <ul>
                {sortedList.map((item) => (
                    <li key={item}>{item}</li>
                ))}
            </ul>
            <button onClick={handleClick}>Click me</button>
        </div>
    );
}
```

In this example, `sortedList` is memoized using `useMemo` to avoid sorting the list on every render. `handleClick` is memoized using `useCallback` to avoid creating a new function on every render.

</details>

<details>
<summary><b>Arrow Functions	Traditional Functions</b></summary>

| Feature                | Arrow Functions                                                                                                                                                              | Traditional Functions                                                                                                                                                                                        |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Syntax**             | `const add = (a, b) => a + b;`                                                                                                                                               | `function add(a, b) { return a + b; }`                                                                                                                                                                       |
| **Example**            | `const add = (a, b) => a + b; console.log(add(2, 3)); // 5`                                                                                                                  | `function add(a, b) { return a + b; } console.log(add(2, 3)); // 5`                                                                                                                                          |
| **`arguments` Object** | No own `arguments` object; inherits from scope                                                                                                                               | Has its own `arguments` object                                                                                                                                                                               |
| **Example**            | `const showArgs = () => { console.log(arguments); // ReferenceError: arguments is not defined }; showArgs(1, 2, 3);`                                                         | `function showArgs() { console.log(arguments); // Logs all arguments passed } showArgs(1, 2, 3); // Logs [1, 2, 3]`                                                                                          |
| **Implicit Return**    | Can implicitly return a value if single expression                                                                                                                           | Requires explicit `return` statement                                                                                                                                                                         |
| **Example**            | `const square = x => x * x; console.log(square(4)); // 16`                                                                                                                   | Traditional functions require explicit `return`, so this feature does not apply.                                                                                                                             |
| **Explicit Return**    | Requires curly braces and `return` for multiple statements                                                                                                                   | Requires `return` for all return values                                                                                                                                                                      |
| **Example**            | `const multiply = (a, b) => { const result = a * b; return result; }; console.log(multiply(2, 3)); // 6`                                                                     | `function multiply(a, b) { const result = a * b; return result; } console.log(multiply(2, 3)); // 6`                                                                                                         |
| **Constructor Usage**  | Cannot be used as constructors (`new` keyword)                                                                                                                               | Can be used as constructors (`new` keyword)                                                                                                                                                                  |
| **Example**            | `const ArrowClass = () => {}; const instance = new ArrowClass(); // TypeError: ArrowClass is not a constructor`                                                              | `function TraditionalClass() { this.value = 42; } const instance = new TraditionalClass(); console.log(instance.value); // 42`                                                                               |
| **`this` Binding**     | Lexical scoping; `this` is inherited from surrounding context                                                                                                                | Dynamic; `this` is determined by how function is called                                                                                                                                                      |
| **Example**            | `` const ArrowFunction = () => { this.value = 42; setTimeout(() => { console.log(this.value); // `this` refers to ArrowFunction context }, 1000); }; new ArrowFunction(); `` | `` function TraditionalFunction() { this.value = 42; setTimeout(function() { console.log(this.value); // `this` refers to global object (undefined in strict mode) }, 1000); } new TraditionalFunction(); `` |

</details>

#### Template

<details>
<summary><b>clickme</b></summary>
Hi
</details>
