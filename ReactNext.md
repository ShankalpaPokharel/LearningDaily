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
```
</details>

<details>
<summary> <b> React setState Management (Direct update and Using function) </b></summary>

**Always Use the Functional Version of `setState`:**
- When updating state in React, especially if the new state depends on the previous state, it's best to use the functional version of `setState`.
- React batches multiple state updates within the same event handler or lifecycle method, which means if you use the regular `setState`, some updates might be lost.
  
  **Example:**
  ```jsx
  // Incorrect way (might cause bugs if count depends on previous state)
  setCount(count + 1);
  setCount(count + 1); 

  // Correct way
  setCount(prevCount => prevCount + 1);
  setCount(prevCount => prevCount + 1);
  ```
  In the correct version, React ensures that `prevCount` is up-to-date each time the state is set.

</details>

<details>
<summary><b>AbortController in `useEffect`</b></summary>

**Use Case:**
- `AbortController` is useful for canceling ongoing network requests when a component unmounts or when a new request needs to replace the old one.
- This prevents memory leaks and ensures that outdated requests do not affect your app's behavior.

**Scenario:**
- Suppose you have a search feature that makes an API call every time the user types a character. If the user types quickly, the previous requests should be aborted to avoid unnecessary processing and potential bugs.

**Example:**
```jsx
import { useEffect, useState } from 'react';

function SearchComponent() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState([]);

  useEffect(() => {
    const controller = new AbortController();

    const fetchData = async () => {
      try {
        const response = await fetch(`https://api.example.com/search?q=${query}`, {
          signal: controller.signal
        });
        const data = await response.json();
        setResults(data.results);
      } catch (err) {
        if (err.name === 'AbortError') {
          console.log('Request aborted');
        } else {
          console.error('Fetch error:', err);
        }
      }
    };

    if (query) {
      fetchData();
    }

    // Cleanup function to abort the fetch if the component unmounts or query changes
    return () => {
      controller.abort();
    };
  }, [query]);

  return (
    <div>
      <input value={query} onChange={(e) => setQuery(e.target.value)} />
      <ul>
        {results.map(result => (
          <li key={result.id}>{result.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

**Related Points:**
- The `AbortController` is especially useful in scenarios where network requests are frequent, such as search inputs, infinite scrolling, or any component that re-fetches data based on user interaction.
- Always remember to clean up the controller in the return statement of `useEffect` to avoid trying to update the state after the component has unmounted.
</details>


<details>

<summary><b>Handling API Errors Effectively</b></summary>

### **Handling API Errors Effectively**

#### **Scenario:**
When interacting with APIs, you may encounter situations where the server returns an error status code (e.g., 404 Not Found, 500 Internal Server Error) without throwing a JavaScript error. This happens because the server responds with an error in the body but does not throw a network-level exception that would be caught by a `catch` block.

#### **Example:**

Imagine you have an API endpoint `/api/user` that occasionally returns a 404 error when the user is not found. A `fetch` request to this endpoint might return an error status but not throw an exception.

```javascript
async function fetchUserData(userId) {
  try {
    const response = await fetch(`/api/user/${userId}`);
    if (!response.ok) {
      // Handle non-success status codes
      return null; // Return null to indicate an error
    }
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Fetch error:", error);

  }
}
```

#### **Solution:**

1. **Check Response Status:**
   Use `response.ok` to determine if the HTTP response indicates success (status code 200-299). If not, handle the error case by returning a sentinel value like `null`.

   ```javascript
   if (!response.ok) {
     return null; // Indicates an error status
   }
   ```

2. **Handle Errors on the Frontend:**
   Check for the sentinel value (e.g., `null`) on the frontend and take appropriate action, such as displaying an error message to the user.

   ```javascript
   async function loadUser(userId) {
     const user = await fetchUserData(userId);
     if (user === null) {
       console.log("Failed to fetch user data.");
     } else {
       console.log("User data:", user);
       // Process the fetched user data
     }
   }
   ```

#### **Reason:**

- **Non-Exception Errors:**
  HTTP status errors (like 404 or 500) are part of the response object, not JavaScript exceptions. Therefore, `catch` blocks will not handle them unless they are network-level errors (e.g., a failed network request).

- **Graceful Error Handling:**
  By checking `response.ok`, you can handle HTTP errors directly and avoid assuming that all non-successful responses will throw exceptions. This approach helps in managing UI states or fallback logic effectively.

- **User Experience:**
  Handling errors gracefully improves user experience by providing meaningful feedback rather than failing silently or crashing.

#### **Additional Notes:**

- **Fallback Values:**
  Using `null` or other fallback values helps in distinguishing between successful and failed responses.

- **Network Errors:**
  Ensure that network-level issues are also handled by a `catch` block, which catches errors such as connectivity issues.

- **Consistency:**
  Keep error handling consistent across different API calls in your application to maintain a uniform approach to managing failures.

</details>

<details>

<summary> <b>View More functionality</b> </summary>

```js
const [productList, setProductList] = useState(products);
const [visibleCount, setVisibleCount] = useState(8);
const [page, setPage] = useState(1);
const [loading, setLoading] = useState(false);
const [viewMore, setViewMore] = useState(true);

const loadMoreBlogs = async () => {
  try {
    setLoading(true);
    const newVisibleCount = visibleCount + 4;

    if (newVisibleCount > productList.length && productList.length % 8 === 0) {
      const newBlogs = await getProducts(page, 8);
      if (newBlogs.length > 0) {
        setProductList(prevProducts => [...prevProducts, ...newBlogs]);
        setPage(prevPage => prevPage + 1);
      } else {
        setVisibleCount(productList.length);
      }
    } else if (productList.length < visibleCount) {
      setViewMore(false);
    }

    setVisibleCount(newVisibleCount);

    if (productList.length < visibleCount) {
      console.log("Condition met");
      setViewMore(false);
    }

    setLoading(false);
  } catch (error) {
    setLoading(false);
  }
};

useEffect(() => {
  if (productList.length < visibleCount) {
    setViewMore(false);
  }
}, [productList, visibleCount]);
```
</details>


### Add google translater in Next App
---

<details>

<summary>Add google translater in Next App</summary>


1. Make a GoogleTranslate.tsx component 

```tsx

"use client";

import { useEffect } from "react";

declare global {
  interface Window {
    google: any;
    googleTranslateElementInit: () => void;
  }
}

const GoogleTranslate: React.FC = () => {
  useEffect(() => {
    if (!window.googleTranslateElementInit) {
    const googleTranslateElementInit = () => {
      if (window.google && window.google.translate) {
        new window.google.translate.TranslateElement(
          {
            pageLanguage: "en",
            layout: window.google.translate.TranslateElement.InlineLayout.HORIZONTAL,
            autoDisplay: false // Prevent automatic display of the widget
          },
          "google_translate_element"
        );
      }
    };

    const addScript = () => {
      const script = document.createElement("script");
      script.type = "text/javascript";
      script.async = true;
      script.src = "//translate.google.com/translate_a/element.js?cb=googleTranslateElementInit";
      document.body.appendChild(script);
      window.googleTranslateElementInit = googleTranslateElementInit;
    };

    addScript();
  }
  }, []);

  return <div id="google_translate_element" className="flex"></div>;
};

export default GoogleTranslate;

```

2. Add it in the layout

```tsx
export default async function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  const settingData = await getSettingData()
  return (
    <html lang="en">
      <body className={}>
      <GoogleTranslate/> //here
        <PageTop settingData={settingData} />
        <Suspense fallback={<Loading />}>
          {children}
        </Suspense>
        <Footer/>
        <FooterBottom />
      </body>
    </html>
  );
}
```

3. Some style in global.css (not mendetory)
```css

#google_translate_element {
    display: flex;
    align-items: center;
  }
  
.goog-te-gadget {
    display: flex;
  }
.goog-te-menu-frame {
    display: none !important;
  }
  
```

</details>