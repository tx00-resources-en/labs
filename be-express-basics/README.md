# Express Web Development Lab

## Express Web Development Lab (Part 1/3)

In this part, you will learn how to create a simple Express app with two endpoints—one returning simple text and the other returning JSON. You'll also explore how to use `nodemon` for automatic server restarts during development. Along the way, we'll explain important concepts like port, `app.get()`, `res.json()`, and `res.send()`.

### Step 1: Set Up the Project

1. Create a new directory for your project and navigate to it in the terminal.

2. Initialize a new Node.js project by running:
   ```
   npm init -y
   ```

3. Install `express` as a dependency:
```sh
npm install express
```

4. Install `nodemon` as a development dependency:
```sh
npm install nodemon --save-dev
```

### Step 2: Create the Express App

1. Create a file named `app.js` in your project directory.

2. Add the following code to set up the Express app:
   ```javascript
   const express = require('express');
   const app = express();
   const port = 3001;

   // Endpoint 1: Text Response
   app.get('/text', (req, res) => {
     res.send('This is a simple text response.');
   });

   // Endpoint 2: JSON Response
   app.get('/json', (req, res) => {
     const jsonData = {
       message: 'This is a JSON response.',
       timestamp: new Date()
     };

     res.json(jsonData);
   });

   // Start the server
   app.listen(port, () => {
     console.log(`Server is listening on port ${port}`);
   });
   ```

### Step 3: Using Nodemon

1. Open your `package.json` file in a text editor.

2. Add the following line inside the `"scripts"` section:
   ```json
   "dev": "nodemon app.js"
   ```

### Step 4: Understand Key Concepts

1. **Port:** The `port` is a number that defines which endpoint the server should listen on. In this lab, it's set to 3001, so the server listens at `http://localhost:3001`.

2. **`app.get()`:** This method sets up a route for handling HTTP GET requests. It takes two arguments: the route path and a callback function. When a GET request matches the route path, the callback function is executed.

3. **`res.json()` and `res.send()`:**
   - `res.json(data)`: Sends a JSON response. It converts the `data` object to JSON format.
   - `res.send(text)`: Sends a simple text response.

### Step 5: Running the Lab

1. In the terminal, run the server using the `dev` script you added:
```sh
npm run dev
```

2. Open a web browser or use a tool like `curl` to access the endpoints:
   - Text Endpoint: `http://localhost:3001/text`
   - JSON Endpoint: `http://localhost:3001/json`

### Recap

This lab provides a solid foundation for more complex Express applications.


---

## Express Web Development Lab (Part 2/3)

In this section, we'll explore further with `nodemon`, understand how to run the server using `npm start`, delve into why `npm run dev` works while `npm dev` doesn't, implement a simple middleware, and grasp the functioning of middlewares.

### Step 1: Modifying `app.js` with Nodemon

1. Keep the terminal running with the `nodemon`-powered server.

2. Open the `app.js` file in your text editor.

3. Modify the message in the JSON response section:
   ```javascript
   const jsonData = {
     message: 'This is an updated JSON response.',
     timestamp: new Date()
   };
   ```

4. Save the file.

5. Watch the terminal where `nodemon` is running. You should see a message indicating that the server has restarted due to the file change.

### Step 2: Using `npm start` vs `npm run dev`

1. In your `package.json` file, add a script named `"start"`:
```json
"start": "nodemon app.js"
```

2. Save the file.

3. Stop the `nodemon` process in your terminal if it's still running.

4. Start the server using:
```sh
npm start
```

Observe that the server is running. Does it behave the same as `npm run dev`?

> Running your application with `node app.js` is the standard way to start a Node.js application. It's a basic approach, but it lacks the automatic restart functionality of `nodemon`, [More info].(#differences-between-using-nodemon-and-node-appjs)

> The reason why `npm start` works without the `run` keyword (`npm run start`) is because `start` is a special script name recognized by npm. When you define a script named `"start"` in your `package.json` file, you can run it directly using `npm start`, [More info](#npm-start).


### Step 3: Understanding `npm run dev` vs `npm dev`

1. The `npm run` command is used to execute scripts defined in `package.json`.

2. When you use `npm run dev`, it searches for a script named "dev" in your `package.json` and executes it.

3. Using `npm dev` directly would imply that you're trying to run a globally installed package named "dev," which isn't what you intend.

### Step 4: Implementing a Simple Middleware

Middleware functions are functions that have access to the request and response objects, and the `next` function. They can perform tasks, modify the request/response objects, end the request-response cycle, or call the next middleware in the stack.

1. Open your `app.js` file again.

2. Save the following code in `app.js`.

```javascript
const express = require('express');
const app = express();

// BEGIN: Middleware Definition
const requestTime = function (req, res, next) {
  req.requestTime = Date.now();
  next();
};
// END: Middleware Definition

// Adding the Middleware Globally
app.use(requestTime);

// Defining the '/stats' Route
app.get('/stats', (req, res) => {
  let responseText = 'Hello World!<br>';
  responseText += `<small>Requested at: ${req.requestTime}</small>`;
  res.send(responseText);
});

// Start the Server
app.listen(3001, () => {
  console.log('Server is listening on port 3001');
});
```

**Running the Application**

1. Start the server by running:

```sh
npm run dev
```

2. Open your web browser and visit `http://localhost:3001/stats`. You should see a response that includes "Hello World!" along with the timestamp of the request.

By using the provided middleware, you've enhanced the `/stats` route to display the timestamp of the request. This demonstrates how middlewares can modify request and response objects, adding functionality to your Express application.

###  Step 5: Explanation

The middleware `requestTime` adds a `requestTime` property to the request object (`req`). This property holds the timestamp of when the request was made. It then calls the `next()` function to pass control to the next middleware or route handler.

2. **Adding the Middleware:** In your Express app, you added the `requestTime` middleware using `app.use(requestTime)`. This attaches the middleware globally to all routes.

3. **Using the Middleware:** The `requestTime` property added by the middleware can be accessed in your route handlers. In this case, it's used to display the timestamp when handling the `/stats` route.

4. **Creating the `/stats` Route:** The `/stats` route responds with a text containing "Hello World!" and the timestamp of the request.


### Recap

You're now equipped with valuable tools and knowledge for building more sophisticated Express applications. 


---

## npm start

The reason why `npm start` works without the `run` keyword (`npm run start`) is because `start` is a special script name recognized by npm. When you define a script named `"start"` in your `package.json` file, you can run it directly using `npm start`.

Here's how it works:

1. **Special Scripts:**
   npm has a set of special scripts that can be executed without using the `run` keyword. These include `"start"`, `"test"`, and `"stop"`. When you use these special script names, npm automatically knows how to execute them.

2. **"start" Script:**
   When you define a `"start"` script in your `package.json` file, it's intended to start your application. This is a common convention for web development projects. When you run `npm start`, npm internally knows to execute the `"start"` script.

3. **Other Scripts:**
   For scripts that aren't one of the special script names (e.g., `"dev"`, `"build"`), you need to use the `run` keyword to explicitly tell npm that you're executing a script. For example, you would use `npm run dev` to execute a script named `"dev"`.

In summary, `npm start` is a special case where npm recognizes it as a default command for starting your application. This simplifies the command you need to run in order to start your project compared to using `npm run start`.

---
## Differences between using `nodemon` and `node app.js`

**Using `nodemon`**

`nodemon` is a utility that helps in development by monitoring changes in your files and automatically restarting your application when changes are detected. This is extremely useful as it saves you the trouble of manually stopping and restarting your server every time you make code changes.

1. **Convenience:** With `nodemon`, you don't need to manually restart your application every time you make changes to your code. The tool detects changes and handles the restart for you.

2. **Development Workflow:** During development, you often make frequent changes to your code. With `nodemon`, you can see your changes immediately without the hassle of stopping and restarting the server.

3. **Command:** To run your application using `nodemon`, you use the command:
   ```
   nodemon app.js
   ```
   This monitors your `app.js` file and restarts the application whenever you save changes.

**Using `node app.js`**

Running your application with `node app.js` is the standard way to start a Node.js application. It's a basic approach, but it lacks the automatic restart functionality of `nodemon`.

1. **Manual Restart:** When you use `node app.js`, you need to manually stop the server (Ctrl+C) and then restart it (using the same command) each time you make changes.

2. **Simplicity:** This method is straightforward and can be suitable for smaller projects where you don't expect to make frequent changes.

3. **Command:** To run your application using `node app.js`, you use the command:
   ```
   node app.js
   ```

**Comparison and Use Cases:**

- **Use `nodemon` when:**
   - You are actively developing and want a smoother development experience.
   - You want your server to automatically restart whenever you make code changes.
   - You're working on a project with multiple files or a more complex structure.

- **Use `node app.js` when:**
   - You're running your application in a more controlled or production-like environment.
   - You want a simpler way to run your application without automatic restarts.

`nodemon` enhances your development workflow by providing automatic restarts, which is extremely helpful for projects where you're frequently making code changes. On the other hand, `node app.js` is suitable for basic situations where automatic restarts are not necessary.