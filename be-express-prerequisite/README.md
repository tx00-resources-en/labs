# JavaScript Lab

In this lab, you'll learn some fundamental concepts of JavaScript while working in the Node.js environment.

### Part 1: Template Literals

1. **Create a New File:**
   - Open a text editor and create a new file named `node.js`.

2. **Declare a Variable:**
   - Inside `node.js`, write: `const name = "YourName";` (Replace `"YourName"` with your actual name.)

3. **Use Template Literals:**

Below the variable declaration, write: 
```js
const message = `Hello, my name is ${name}.`;
```

1. **Print the Message:**
   - Add: `console.log(message);` on the next line.

2. **Run Your Code:**
   - Open your terminal, navigate to the directory containing `node.js`, and run: `node node.js`.
   - You should see the message printed in the console.

### Part 2: JSON vs JavaScript Objects

1. **Declare an Object:**

After the previous part, write: 
```js
const person = { name: "John", age: 25, email: "john@example.com" };
```

1. **Convert to JSON:**
   - Write: `const jsonPerson = JSON.stringify(person);`
   - `jsonPerson` now holds the JSON representation of the `person` object.

2. **Print JSON:**
   - Add: `console.log(jsonPerson);`

3. **Parse JSON:**
   - Write: `const jsonString = '{"name": "Alice", "age": 30, "email": "alice@example.com"}';`
   - `jsonString` contains JSON-formatted data.

4. **Convert JSON to Object:**
   - Write: `const parsedPerson = JSON.parse(jsonString);`
   - `parsedPerson` is now a JavaScript object.

5. **Print Parsed Object:**
   - Add: `console.log(parsedPerson);`

### Part 3: Functions as First-Class Citizens

1. **Define an Addition Function:**
   - After the previous part, write: 
     ```javascript
     function add(a, b) {
       return a + b;
     }
     ```

2. **Assign to a Variable:**
   - Write: `const calculate = add;`

3. **Invoke the Function:**
   - Write: `const sum = calculate(5, 3);`
   - Add: `console.log("Sum:", sum);`

4. **Define an Operation Function:**
   - Write:
     ```javascript
     function operate(a, b, operation) {
       return operation(a, b);
     }
     ```

5. **Create a Multiplication Function:**
   - Write:
     ```javascript
     function multiply(a, b) {
       return a * b;
     }
     ```

6. **Use the Operation Function:**
   - Write: 
     ```javascript
     const result = operate(4, 2, multiply);
     console.log("Result of multiplication:", result);
     ```

6. **Returning a Function**

**Define a Function that Returns a Function:**
   - After the previous part, write:
     ```javascript
     function greetPrefix(prefix) {
       return function(name) {
         console.log(\`\${prefix}, \${name}!\`);
       };
     }
     ```

**Create Greeting Functions:**
   - Write:
     ```javascript
     const greetHello = greetPrefix("Hello");
     const greetHi = greetPrefix("Hi");
     ```

**Invoke the Greeting Functions:**
   - Write:
     ```javascript
     greetHello("Alice");
     greetHi("Bob");
     ```

### Finishing Up:
- Save your `node.js` file after completing each part.
- Run your code using the `node node.js` command in the terminal.
- Observe the output for each part to ensure it matches the expected results.

You've completed the lab and learned about template literals, JSON, JavaScript objects, functions as first-class citizens, returning functions, and using callbacks. 

Happy coding!
