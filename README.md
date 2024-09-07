Deployment Guide for any Application
This guide outlines the steps for deploying and updating any application on an Azure Virtual Machine (VM).

Deployment Process
Follow these steps to deploy the backend and frontend applications on the Azure VM:

1. Login to Azure VM
Use SSH to log into the Azure VM. Replace the placeholders with your actual SSH key and IP address:

   ssh -i <your-key-file.pem> azureuser@<your-vm-ip>

2. Install Required Tools
Ensure the following are installed on the VM:

Node.js
Nginx
PM2 (Process Manager)

3. Clone the Repository
Clone the project repository from GitHub into the VM. Replace <repository-url> with the actual URL of the repository:

    git clone <repository-url>

4. Update Nginx Configuration
Update the Nginx configuration file as necessary for your setup (e.g., /etc/nginx/sites-available/default).

5. Start Backend Application
Navigate to the backend directory and start the application using PM2:

    pm2 start server.js

6. Start Frontend Application
Navigate to the frontend directory and start the application using PM2:

    cd frontend
    pm2 start npm --name "react-writebing" -- start


Pushing Updates to Production
Follow these steps to push updates to the production environment:

1. Login to Azure VM
Log into the Azure VM using SSH. Replace the placeholders with your actual SSH key and IP address:

    ssh -i <your-key-file.pem> azureuser@<your-vm-ip>

2. Navigate to Project Directory
Go to the project directory:

    cd writebing

3. Pull Latest Changes from GitHub
Pull the latest changes from the repository:
    git pull

4. Rebuild Frontend (If Necessary)
If changes are made in the frontend, navigate to the frontend directory and run:

    cd frontend
    npm run build

5. Check Application Status
Ensure that the backend and frontend processes are running in the background using PM2:

    pm2 status
    pm2 monit
    pm2 logs

