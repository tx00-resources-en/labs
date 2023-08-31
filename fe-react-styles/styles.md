# React Styling

### Setting Up Your Environment

Please choose only **one** alternatives

1. First method

Open your terminal and run:
```sh
npx degit tx00-web/labs/react-starter#main styles-demo
cd styles-demo
```

2. Second method
Open your terminal and run:

```sh
npx create-react-app styles-demo
cd styles-demo
```


### Inline Styles

1. Open the `src/App.js` file. This is where the main component of your React app is defined.

2. Replace the existing content of the `App` component with the following code:
```jsx
const App = () => {
  const headingStyle = {
 color: 'blue',
 fontSize: '24px',
 textAlign: 'center',
  };

  return (
 <div>
<h1 style={headingStyle}>Inline Styles</h1>
<p style={{ color: 'green' }}>This is a green paragraph.</p>
 </div>
  );
};

export default App;
```
In this code, you define the `App` component using a functional component. You create an object called `headingStyle` that holds CSS properties for the heading. This object is then used as an inline style for the `<h1>` element. The `<p>` element also has an inline style directly defined.

**Running the App**

- Save your changes to the files.
- In the terminal, start the development server with the command:
```bash
npm install
npm start
```

- Open your web browser and navigate to `http://localhost:3000` to see the different styles in action.


### External CSS File**

1. Create a new CSS file named `styles.css` in the `src` folder. This file will contain your external styles.

2. Open the newly created `src/styles.css` file and add the following CSS rules:
```css
.external-heading {
  color: red;
  text-align: center;
}
```
In this CSS code, you define a class selector `.external-heading` with styling rules that set the text color to red and align it to the center.

3. Go back to the `src/App.js` file.

4. Import the `styles.css` file at the top of the file:
```jsx
import './styles.css';
```
By importing the CSS file, you make its styles available for use in your React components.

5. Modify the `App` component to use the styles from the external CSS file:
```jsx
const App = () => {
  return (
 <div>
<h1 className="external-heading">External CSS Styles</h1>
 </div>
  );
};
```
Here, you apply the `external-heading` class to the `<h1>` element and the `external-paragraph` class to the `<p>` element. These classes are defined in the `styles.css` file you imported.

**Running the App**

- Save your changes to the files.
- In the terminal, start the development server with the command:
```bash
npm install
npm start
```

- Open your web browser and navigate to `http://localhost:3000` to see the different styles in action.


### CSS Modules

1. Rename the existing `src/styles.css` file to `src/styles.module.css`. This renaming is essential to enable CSS Modules.

2. Open the `src/styles.module.css` file and update the class names and styles as follows:
```css
.module-heading {
  color: purple;
  text-align: center;
}
```
In this file, you define a class selector `.module-heading` with new styles that set the text color to purple and align it to the center.

- Go back to the `src/App.js` file.
- Import the `styles.module.css` file at the top of the file using the following syntax:
```jsx
import styles from './styles.module.css';
```
By using the `import styles from` syntax, you're importing the CSS module as an object that holds class names as properties.

- Modify the `App` component to use the CSS module styles:
```jsx
const App = () => {
  return (
    <div>
      <h1 className={styles.moduleHeading}>CSS Modules</h1>
    </div>
  );
};

```
In this code, you apply the CSS module classes `module-heading` and `module-paragraph` to the respective elements. You use the syntax `styles.moduleHeading` to access the class from the imported `styles` object.
> Did you notice any differences? [More explanantion here](https://upmostly.com/tutorials/what-are-css-modules-in-react)

**Running the App**

- In the terminal, start the development server with the command:
```bash
npm install
npm start
```

- Open your web browser and navigate to `http://localhost:3000` to see the different styles in action.


