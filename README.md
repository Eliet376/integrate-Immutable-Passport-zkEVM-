# Integrate-Immutable-Passport-zkEVM-
A guide that teaches users how to integrate Immutable Passport into their application.
### Integrating Immutable Passport into Your Application: A Step-by-Step Guide

In this guide, we will walk you through the process of integrating Immutable Passport into your application. Immutable Passport is a powerful authentication and transaction initiation tool that can elevate your app's security and functionality. Let's get started!

#### **Prerequisites:**
1. **Node.js and npm:** Ensure you have Node.js and npm (Node Package Manager) installed on your system.
2. **GitHub Account:** You'll need a GitHub account to access the Immutable Developer Hub and publish your sample app.

### Step 1: Setting Up Your Application

1. **Create a Simple Application:**
   - Create a new directory for your project or clone a repository for your existing app.
   - Inside your project directory, create an `index.html` file and a `script.js` file.

   ```html
   <!-- index.html -->
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Immutable Passport Integration</title>
   </head>
   <body>
       <h1>Immutable Passport Integration</h1>
       <button id="loginBtn">Login</button>
       <button id="logoutBtn">Logout</button>
       <p>User ID Token: <span id="userIdToken"></span></p>
       <p>Access Token: <span id="accessToken"></span></p>
       <p>User Nickname: <span id="userNickname"></span></p>

       <script src="script.js"></script>
   </body>
   </html>
   ```

2. **Register Your Application:**
   - Go to the Immutable Developer Hub and register your application.
   - Obtain your `CLIENT_ID` after registering your app.

### Step 2: Integrating Immutable Passport

1. **Install Immutable Passport Client:**
   ```bash
   npm install @immutable/passport
   ```

2. **Initialize Immutable Passport in Your App:**
   ```javascript
   // script.js
   const { ImmutablePassport } = require('@immutable/passport');

   const passport = new ImmutablePassport({
       clientId: 'YOUR_CLIENT_ID_FROM_DEVELOPER_HUB',
       redirectUri: 'http://localhost:3000/callback',
       scopes: ['openid', 'profile'], // Adjust scopes as per your requirements
   });
   ```

3. **Login a User with Passport:**
   ```javascript
   // script.js
   const loginButton = document.getElementById('loginBtn');
   loginButton.addEventListener('click', async () => {
       await passport.login();
       const userIdToken = await passport.getIdToken();
       const accessToken = await passport.getAccessToken();
       const userNickname = await passport.getUserInfo().nickname;

       document.getElementById('userIdToken').textContent = userIdToken;
       document.getElementById('accessToken').textContent = accessToken;
       document.getElementById('userNickname').textContent = userNickname;
   });
   ```

4. **Logout a User:**
   ```javascript
   // script.js
   const logoutButton = document.getElementById('logoutBtn');
   logoutButton.addEventListener('click', () => {
       passport.logout();
       // Clear displayed user info
       document.getElementById('userIdToken').textContent = '';
       document.getElementById('accessToken').textContent = '';
       document.getElementById('userNickname').textContent = '';
   });
   ```

5. **Initiate a Transaction with Passport:**
   ```javascript
   // script.js
   // Assuming you have a button with id 'transactionBtn' in your HTML
   const transactionButton = document.getElementById('transactionBtn');
   transactionButton.addEventListener('click', async () => {
       const transactionHash = await passport.initiateTransaction('placeholder string');
       console.log('Transaction Hash:', transactionHash);
   });
   ```

### Step 3: Run Your Application

1. **Start Your Application:**
   ```bash
   npm start
   ```

2. **Open Your Browser:**
   - Open your web browser and go to `http://localhost:3000`.
   - Click the **Login** button to initiate the Immutable Passport login process.
   - After logging in, you can see the user information displayed on the webpage.
   - Click the **Transaction** button to initiate a transaction and check the transaction hash in the console.

Congratulations! You have successfully integrated Immutable Passport into your application. Feel free to explore more Passport functionalities and customize your app further. Don't forget to commit your changes and push them to your GitHub repository to share your implementation with the community.

For more detailed information and advanced features, refer to the official Immutable Passport documentation.

Happy coding! 🚀
