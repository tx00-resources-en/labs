# Lab: Creating an Express.js App with Error Handling and Static Assets

In this lab, you will create a simple Express.js application with two GET endpoints that return text, handle error pages, and serve static assets. 

**Step 1: Set Up the Project**

1. **Create a Project Directory**: Open your terminal and create a new directory for your project.

```sh
mkdir express-lab
cd express-lab
```

2. **Initialize the Project**: Initialize a new Node.js project using `npm init`. Follow the prompts to set up your project. Press Enter to accept the default values for most prompts.

```sh
npm init
```

**Step 2: Install Dependencies**

1. **Install Express.js**: Install the `express` package as a dependency for your project.

```sh
npm install express
```

2. **Install Nodemon (Development Dependency)**: Install `nodemon` as a development dependency. It will automatically restart the server whenever you make changes to your code.

```sh
npm install nodemon --save-dev
```

**Step 3: Create App Files**

1. **Create Main Server File**: Create a file named `server.js` in the project directory. This will be the main entry point for your application.

```javascript
   // server.js

   const express = require('express');
   const path = require('path');

   const app = express();
   const PORT = 3001;

   app.use(express.static('public'));

   app.get('/endpoint1', (req, res) => {
     res.send('This is the first endpoint.');
   });

   app.get('/endpoint2', (req, res) => {
     res.send('This is the second endpoint.');
   });

   app.use((req, res, next) => {
     res.status(404).send("Sorry, the requested page couldn't be found.");
   });

   app.use((err, req, res, next) => {
     console.error(err.stack);
     res.status(500).send('Something went wrong on the server.');
   });

   app.listen(PORT, () => {
     console.log(`Server is running on port ${PORT}`);
   });
```

In this code:

- We import the `express` module and create an instance of the Express application.
- We use the `express.static` middleware to serve static files from the "public" directory.
- We define two GET endpoints, `/endpoint1` and `/endpoint2`, each sending a simple text response.
- We define a middleware to handle 404 Not Found errors. If none of the previous routes matched the request, this middleware will be triggered.
- We define a middleware to handle general errors. If an error occurs during request processing, this middleware will be triggered, logging the error and sending a 500 Internal Server Error response.
- Finally, the app listens on port 3001 for incoming requests.

2. **Create a "public" Directory**: Create a directory named "public" in the project directory. 

> Inside this directory, you can add your static assets such as CSS, JavaScript, and images.

3. Inside the "public" directory, create an HTML file named `index.html`:

   ```html
   <!-- public/index.html -->

   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <link rel="stylesheet" href="styles.css">
     <title>Express App</title>
   </head>
   <body>
     <h1>Hello from Express App!</h1>
   </body>
   </html>
   ```

4. Inside the "public" directory, create a CSS file named `styles.css`:

   ```css
   /* public/styles.css */

   body {
     font-family: Arial, sans-serif;
     background-color: #f5f5f5;
     text-align: center;
     padding: 20px;
   }

   h1 {
     color: #333;
   }
   ```

**Step 4: Running the App**

1. **Run the App with Nodemon**: Start the server using `nodemon` to automatically restart it when you make changes.

```sh
npx nodemon server.js
```

2. **Access Endpoints**: Open your web browser and visit the following URLs to see the endpoints in action:

   - [http://localhost:3000/endpoint1](http://localhost:3000/endpoint1)
   - [http://localhost:3000/endpoint2](http://localhost:3000/endpoint2)

3. **Access Static Assets**: visit the following URL. You should see a simple page with a heading styled using the CSS.

   - [http://localhost:3000/](http://localhost:3000/) 
   

**Step 5: Handling Errors**

1. **Testing 404 Error**: If you visit a URL that doesn't correspond to an existing endpoint, you will see the 404 error page.

   - [http://localhost:3000/nonexistent](http://localhost:3000/nonexistent)

2. **Testing 500 Error**: Introduce an intentional error in your code to trigger a server error. For example, you can add the following line inside your `app.get('/endpoint1' ...)` route:

```javascript
throw new Error('Intentional server error');
```

Now visit [http://localhost:3000/endpoint1](http://localhost:3000/endpoint1) to see the 500 error page.

**Explanation of Concepts:**

- **Express Middleware**: Middleware functions in Express are functions that have access to the `request` and `response` objects. They can perform various tasks, such as modifying request/response objects, executing code, and more. In the example code, `express.static` is a built-in middleware that serves static files from a directory.
- **Serving Static Files**: The `express.static` middleware is used to serve static assets like HTML, CSS, JavaScript, and images. It takes a directory path as an argument and automatically serves any files in that directory to the client.
- **Routing and Endpoints**: In Express, you define routes and endpoints to handle different types of incoming requests. Each route is associated with a specific HTTP method (GET, POST, etc.) and a URL pattern. The example code defines two simple GET endpoints, `/endpoint1` and `/endpoint2`, each sending a text response.
- **Error Handling Middleware**: Express provides a way to handle errors through middleware functions. The example code includes two error handling middlewares: one for 404 Not Found errors and another for general errors (500 Internal Server Error).

**Step 6: Create an npm Script**

1. Open your `package.json` file in the project directory.

2. Add the following line inside the `"scripts"` section:

   ```json
   "scripts": {
     "dev": "nodemon server.js"
   }
   ```

   Your `package.json` file should now look something like this:

   ```json
   {
     "name": "express-app",
     "version": "1.0.0",
     "description": "An example Express.js app",
     "main": "server.js",
     "scripts": {
       "dev": "nodemon server.js"
     },
     "dependencies": {
       "express": "^4.17.1"
     },
     "devDependencies": {
       "nodemon": "^2.0.13"
     },
     "license": "MIT"
   }
   ```

3. Save the `package.json` file.

**Step 7: Running the Server with the Custom Script**

1. Open your terminal.

2. To start the server using the custom script, run:

```sh
npm run dev
```

This will start the server using nodemon and automatically restart it whenever you make changes to the code.


By using the `npm run dev` script, you can start the server more conveniently and consistently during development.

**Recap**
You've successfully created an Express.js application with error handling, static assets, and automatic server restarts using `nodemon`. This lab covers the basics of building a simple web application with Express.js, serving static files, and handling different types of errors.