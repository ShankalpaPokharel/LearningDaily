<details>
<summary><b>React State Updates are Asynchronous</b></summary>


## **React State Updates are Asynchronous**

### **State Updates are Asynchronous**

In React, `useState` updates are asynchronous and do not immediately reflect in the current render.

### **Issue**

Trying to use the state immediately after calling the state setter will show the old value, not the updated one.

### **Solution 1: Use `useEffect`**

Use the `useEffect` hook to perform actions with the updated state:

```jsx
useEffect(() => {
  // Actions with updated state
  console.log(count);
}, [count]); // Runs when `count` changes
```
### **Solution 2:** Use a functional update to compute new state based on the previous state:

```jsx
const handleClick = () => {
  setCount(prevCount => {
    console.log(prevCount); // Logs previous count
    return prevCount + 1;
  });
};

```

### **useReducer**
Similar to `useState`, updates to state in `useReducer` are `asynchronous`.

**Issue:** Trying to access the updated state immediately after dispatching an action may show the old state.

**Solution:**

Use useEffect to perform actions with the updated state if needed.
Use a callback or middleware to handle complex state changes if necessary.


**Summary :** To handle the updated state correctly, use useEffect for side effects or functional updates for state calculations.


</details>


<details>
<summary><b>Page Not Found in Next.js</b></summary>

In Next.js, to handle a "Page Not Found" scenario, you can create a `not-found.tsx` file in the `app` folder or in the respective page folder, just like a regular component.

Here's how you can use it:

```tsx
import { notFound } from "next/navigation";

export default function IndividualBlog({ individualBlog }: { individualBlog: blogType }) {
  if (!individualBlog) {
    return notFound();
  }
  // Render your component here
}
