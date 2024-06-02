
# 🚀 Deploying a Full-Stack Application on Render.com

Guide to How I deploy my full-stack application using Render.com:

## Prerequisites

- 🐙 A GitHub account with your full-stack project repository.
- 🌐 A Render.com account.
- 🛠️ TablePlus for database management.

## Deployment Steps

### 1. Configure Your `package.json`

To ensure your full-stack application (both frontend and backend) works well on Render, you need to update your `package.json` file:

1. **Add Build and Start Scripts**:
   - Ensure you have a `build` script that compiles your frontend and a `start` script that runs your backend.

```json
{
  "scripts": {
    "start": "node server.js", // or your server start command
    "build": "cd frontend && npm install && npm run build"
  }
}
```

2. **Update the `start` Script**:
   - Modify the `start` script to serve your built frontend files.

For example, if you’re using Express.js, you might update your `server.js` to serve static files from the `frontend/build` directory:

```javascript
const express = require('express');
const path = require('path');
const app = express();

// Serve static files from the React frontend app
app.use(express.static(path.join(__dirname, 'frontend/build')));

// Serve the index.html file for any unknown paths
app.get('*', (req, res) => {
  res.sendFile(path.join(__dirname, 'frontend/build', 'index.html'));
});

const port = process.env.PORT || 5000;
app.listen(port, () => {
  console.log(`Server is up on port ${port}`);
});
```

### 2. Set Up Your Web Service

1. **🔑 Log in to Render**: Go to [Render.com](https://render.com) and log in.
2. **➕ Create a New Web Service**:
   - Click **"New"** and select **"Web Service"**.
   - Connect your GitHub account and choose the repository with your full-stack project.
   - Configure the service:
     - **Name**: Give your service a name.
     - **Region**: Choose the closest region to your users.
     - **Branch**: Select the branch to deploy (usually `main` or `master`).
     - **Build Command**: `npm run build`.
     - **Start Command**: `npm start`.

### 3. Set Up Your PostgreSQL Database

1. **💾 Create a New PostgreSQL Database**:
   - Click **"New"** and select **"PostgreSQL"**.
   - Name your database and create it.
   - Save the database URL and credentials.

2. **🔧 Configure Your Application**:
   - Update your backend code to use the database URL and credentials.
   - Manage and interact with your database using TablePlus.

### 4. Environment Variables

1. **🔑 Add Environment Variables**:
   - Add necessary environment variables (e.g., API keys, database URLs).
   - Go to the **"Environment"** tab in your service settings and add the variables.

### 5. Deployment and Testing

1. **🚀 Automatic Deploys**:
   - Render deploys your application on every push to the specified branch.
   - Monitor deploy logs in the Render dashboard.

2. **🧪 Testing**:
   - Test your application using the provided URL to ensure everything is working correctly.

### Additional Configuration (Optional)

1. **🌐 Custom Domain**:
   - Configure a custom domain in the Render dashboard under **"Settings"**.
   - Follow Render’s instructions to point your domain to their servers.

2. **🔒 SSL Certificates**:
   - Render provides free SSL certificates for secure HTTPS connections. Enable SSL in the settings.

---

