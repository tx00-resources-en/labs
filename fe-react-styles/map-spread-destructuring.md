# Lab: `map()`, Spread Operator, and Object Destructuring

## Part 1/2
---

In this part, we'll guide you through three fundamental JavaScript concepts: the `map()` method, the spread operator, and object destructuring. These concepts serve as the foundation of modern JavaScript programming. By the end of this lab, you'll have a solid grasp of how to use them effectively in your code.

**Step 1: Understanding the `map()` Method - Transforming Arrays**

In this step, we'll explore the `map()` method, a powerful tool for transforming array elements by applying a custom function.

1. **Create a Directory and Files**:

Start by creating a new directory for your lab. Open your terminal and execute the following commands:

```bash
mkdir javascript-concepts-lab
cd javascript-concepts-lab 
```

Create a new file named `map.js` in the `javascript-concepts-lab` directory:


2. **Write and Execute Code**:

Open the `map.js` file in your preferred text editor and add the following code:

```javascript
const numbers = [2, 4, 6, 8, 10];

const doubledNumbers = numbers.map((num) => num * 2);

console.log('Original Numbers:', numbers);
console.log('Doubled Numbers:', doubledNumbers);
```

Save the file and run it using Node.js:

```bash
node map.js
```

3. **Explanation**:

In the provided code, we declare an array called `numbers` containing numeric values. Using the `map()` method, we double each number in the array by applying a custom function `(num) => num * 2`. The transformed array is stored in `doubledNumbers`. By logging both the original and transformed arrays, we observe how the `map()` method can efficiently modify array elements.

**Step 2: the Spread Operator**

The second step introduces the spread operator, a tool for merging and expanding arrays.

1. **Create a File**:

Create a new file named `spread.js` within the same directory:

2. **Write and Execute Code**:

Open `spread.js` and add the following code:

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const combinedArray = [...arr1, ...arr2];

console.log('Array 1:', arr1);
console.log('Array 2:', arr2);
console.log('Combined Array:', combinedArray);
```

Run the file using Node.js:

```bash
node spread.js
```

3. **Explanation**:

In this code, we initialize two arrays, `arr1` and `arr2`. We then use the spread operator to merge both arrays into a new array named `combinedArray`. By logging all three arrays, we can observe how the spread operator efficiently expands arrays, providing a concise and intuitive way to combine their contents.

**Step 3: Object Destructuring**

This step illuminates object destructuring, a technique for extracting specific values from objects.

1. **Create a File**:

Create a new file named `destructuring.js` in the same directory:


2. **Write and Execute Code**:

Open `destructuring.js` and add the following code:

```javascript
const person = { name: 'Alice', age: 30, city: 'New York' };

const { name, age } = person;

console.log('Name:', name);
console.log('Age:', age);
```

Run the file using Node.js:

```bash
node destructuring.js
```

3. **Explanation**:

In this code snippet, we define an object called `person` with properties like `name`, `age`, and `city`. By employing object destructuring, we directly extract the `name` and `age` properties into separate variables. Logging these variables demonstrates the power of object destructuring in simplifying access to specific values within objects.

## Part 2/2: more examples
---

### map()

1. **Example 1: Converting Temperatures to Kelvin**:

```javascript
const temperaturesCelsius = [0, 15, 30, 45];

const temperaturesKelvin = temperaturesCelsius.map((celsius) => celsius + 273.15);

console.log('Celsius Temperatures:', temperaturesCelsius);
console.log('Kelvin Temperatures:', temperaturesKelvin);
```

2. **Example 2: Capitalizing Names**:

```javascript
const names = ['alice', 'bob', 'carol'];

const capitalizedNames = names.map((name) => name.charAt(0).toUpperCase());

console.log('Original Names:', names);
console.log('Capitalized Names:', capitalizedNames);
```

### spread operator

1. **Example 1: Adding Elements to a Copy**:

```javascript
const originalArray = [10, 20, 30];
const newArray = [...originalArray, 40, 50];

console.log('Original Array:', originalArray);
console.log('New Array with Additional Elements:', newArray);
```

2. **Example 2: Merging Multiple Arrays**:

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const arr3 = [7, 8, 9];

const mergedArray = [...arr1, ...arr2, ...arr3];

console.log('Array 1:', arr1);
console.log('Array 2:', arr2);
console.log('Array 3:', arr3);
console.log('Merged Array:', mergedArray);
```


### Object Destructuring

1. **Example 1: Extracting Nested Properties**:

```javascript
const person = { name: 'Alice', info: { age: 30, occupation: 'Engineer' } };

const { name, info: { age, occupation } } = person;

console.log('Name:', name);
console.log('Age:', age);
console.log('Occupation:', occupation);
```

2. **Example 2: Extracting Function Parameters from an Object**:

```javascript
function greetUser({ name, age }) {
  console.log(`Hello, ${name}! You're ${age} years old.`);
}

greetUser({ name: 'Bob', age: 25 });
```



