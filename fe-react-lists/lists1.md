# Lab: Exploring Lists and Keys

In this lab, you will be guided to create and rend lists, showcasing the importance of keys, and discussing why they're crucial for optimizing performance and preventing warnings.

**Step 1: Setting Up Your React Environment**

1. **Create a New React Project**:

Please choose only **one** alternatives

1. First method

Open your terminal and run:
```sh
npx degit tx00-web/labs/react-starter#main react-lists-lab
cd react-lists-lab
```

2. Second method
Open your terminal and run:

```sh
npx create-react-app react-lists-lab
cd react-lists-lab
```


2. **Start the Development Server**:
Run the development server to see the default React app:

```bash
npm start
```

Your app should be accessible at `http://localhost:3000`.

**Step 2: Creating and Rendering Lists**

1. **Create a Component for the List**:
In the `src` directory, create a new file named `List.js`. Open it and define a functional component:

```jsx
function List() {
  return (
 <div>
{/* Your list items will go here */}
 </div>
  );
}

export default List;
```

2. **Populate the List**:
Inside the `List` component, add a few list items using JSX:

```jsx


function List() {
  return (
 <div>
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
 </div>
  );
}

export default List;
```

3. **Integrate the List in App**:
Open `src/App.js` and import the `List` component at the top. Replace the default content with your `List` component:

```jsx

import List from './List';

function App() {
  return (
 <div className="App">
<h1>React Lists Lab</h1>
<List />
 </div>
  );
}

export default App;
```

**Step 3: Running the App**

1. **Start the Development Server**:
Run the development server again if it's not already running:

```bash
npm start
```

2. **Explore the List**:
Open your browser and navigate to `http://localhost:3000`. You'll see your list of items rendered on the page.

**Step 4: Understanding the Importance of Keys**

React requires a unique "key" prop for each element in a list to optimize performance and track changes efficiently. Let's understand the significance of keys:

1. **Render a List with No Keys**:
In the `List` component, modify the list items to omit keys:

```jsx
function List() {
  return (
 <div>
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
 </div>
  );
}
```

2. **Observe the Warning**:
Run the app and inspect the browser console. You'll notice a warning about missing keys.

3. **Add Keys to List Items**:
To resolve the warning, add unique keys to each list item:

```jsx
function List() {
  return (
 <div>
<ul>
  <li key="1">Item 1</li>
  <li key="2">Item 2</li>
  <li key="3">Item 3</li>
</ul>
 </div>
  );
}
```

**Conclusion: Learning about Lists and Keys**

You've gained a foundational understanding of creating and rendering lists in React. Additionally, you've experienced the importance of using keys to optimize performance and prevent warnings. Continue building on this knowledge as you explore more advanced concepts in React. 

