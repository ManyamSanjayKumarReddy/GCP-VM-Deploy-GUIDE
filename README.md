


# Deployment Guide for Backend and Frontend on GCP via SSH

This document provides step-by-step instructions to deploy a Node.js backend and a React frontend on a Google Cloud Platform (GCP) VM instance using SSH.

## Prerequisites

- SSH access to your GCP VM instance.
- Node.js and npm installed on the server.
- PM2 (Process Manager for Node.js) installed.
- Nginx installed and configured as a reverse proxy.

## Backend Deployment (Node.js)

### 1. Pull the Latest Code from Git

```bash
git pull
```

*Pulls the latest code from your Git repository into the current directory on your server.*

### 2. Edit the Environment Variables

```bash
sudo nano .env
```

*Opens the `.env` file in a text editor (`nano`) with `sudo` privileges, allowing you to edit environment-specific variables.*

### 3. Switch to Superuser

```bash
sudo su
```

*Switches the current user to the superuser (root) to execute the following commands with elevated permissions.*

### 4. Check the Status of PM2 Processes

```bash
pm2 status
```

*Displays the current status of all PM2 processes.*

### 5. Stop the Existing PM2 Process

```bash
pm2 stop medxbay-b
```

*Stops the PM2 process named `Medxbay-b`, effectively shutting down the current instance of the backend.*

### 6. Start the PM2 Process

```bash
pm2 start medxbay-b
```

*Starts or restarts the backend application using PM2, ensuring it's running under the name `Medxbay-b`.*

## Frontend Deployment (React)

### 1. Navigate to the HTML Directory

```bash
cd /var/www/html
```

*Changes the directory to the location where the frontend files are hosted.*

### 2. Move the Existing Build File to a Backup Location

```bash
sudo mv build.zip /home/sutheesh-s
```

*Moves the existing build file (`build.zip`) to a backup directory (`/home/sutheesh-s`) to ensure it's not overwritten.*

### 3. Delete All Existing Files in the Directory

```bash
sudo rm -rf*
```

*Removes all files and directories in `/var/www/html` to prepare for the new build deployment.*

### 4. Build the Frontend Application

```bash
npm run build
```

*Compiles the React application and generates static files for deployment. The output is usually in the `build` directory.*

### 5. Zip the Build Files

```bash
zip -r build.zip build
```

*Creates a zip file (`build.zip`) of the build directory, making it easier to transfer and deploy.*

### 6. Copy the Build Zip to the Hosting Directory

```bash
sudo cp build.zip /var/www/html
```

*Copies the newly created build zip file to the directory where the frontend files will be served from.*

### 7. Navigate Back to the HTML Directory

```bash
cd /var/www/html/
```

*Makes sure you are in the correct directory for the next step.*

### 8. Unzip the Build Files

```bash
sudo unzip build.zip
```

*Extracts the contents of `build.zip` into the `/var/www/html/` directory, making the frontend files available for serving.*

### 9. Restart the Nginx Service

```bash
sudo service nginx restart
```

*Restarts the Nginx web server, ensuring that it serves the latest version of your frontend application.*

## Conclusion

This `README` provides a comprehensive guide to deploying a Node.js backend and a React frontend on a GCP VM instance using SSH. Following these steps ensures a smooth deployment process.
```

