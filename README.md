

# Deployment Guide for Backend and Frontend on GCP via SSH

This document provides step-by-step instructions for deploying a Node.js backend and a React frontend on a Google Cloud Platform (GCP) VM instance using SSH.

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
*Pull the latest code from your Git repository into the current directory on your server.*

### 2. Edit the Environment Variables

```bash
sudo nano .env
```
*Open the `.env` file in a text editor (`nano`) with `sudo` privileges to edit environment-specific variables.*

### 3. Switch to Superuser

```bash
sudo su
```
*Switch to the superuser (root) to execute the following commands with elevated permissions.*

### 4. Check the Status of PM2 Processes

```bash
pm2 status
```
*Display the current status of all PM2 processes.*

### 5. Stop the Existing PM2 Process

```bash
pm2 stop medxbay-b
```
*Stop the PM2 process named `medxbay-b`, effectively shutting down the current instance of the backend.*

### 6. Start the PM2 Process

```bash
pm2 start medxbay-b
```
*Start or restart the backend application using PM2, ensuring it's running under the name `medxbay-b`.*

## Frontend Deployment (React)

### 1. Upload the Build Zip File

*Upload your frontend build zip file to the server.*

### 2. Delete All Existing Files in the Directory

```bash
sudo rm -rf /var/www/html/*
```
*Remove all files and directories in `/var/www/html` to prepare for the new build deployment.*

### 3. Copy the Build Zip to the Hosting Directory

```bash
sudo cp build.zip /var/www/html
```
*Copy the newly created build zip file to the directory where the frontend files will be served from.*

### 4. Navigate to the HTML Directory

```bash
cd /var/www/html/
```
*Ensure you are in the correct directory for the next step.*

### 5. Unzip the Build Files

```bash
sudo unzip build.zip
```
*Extract the contents of `build.zip` into the `/var/www/html/` directory, making the frontend files available for serving.*

### 6. Restart the Nginx Service

```bash
sudo service nginx restart
```
*Restart the Nginx web server, ensuring it serves the latest version of your frontend application.*

## Conclusion

This document provides a comprehensive guide to deploying a Node.js backend and a React frontend on a GCP VM instance using SSH. Following these steps ensures a smooth deployment process.

---
