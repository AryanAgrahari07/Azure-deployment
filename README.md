Deployment Guide for any Application
This guide outlines the steps for deploying and updating any application on an Azure Virtual Machine (VM). Follow the steps below to ensure a smooth deployment of backend and frontend applications.

Deployment Process
<details> <summary><strong>🔑 Step 1: Login to Azure VM</strong></summary>
Use SSH to log into the Azure VM. Replace the placeholders with your actual SSH key and IP address:
   
   ssh -i <your-key-file.pem> azureuser@<your-vm-ip>
   
</details> <details> <summary><strong>⚙️ Step 2: Install Required Tools</strong></summary>
Ensure the following tools are installed on the VM:

Node.js
Nginx
PM2 (Process Manager)
</details> <details> <summary><strong>📂 Step 3: Clone the Repository</strong></summary>
Clone the project repository from GitHub into the VM. Replace <repository-url> with the actual URL of your repository:

    git clone <repository-url>

</details> <details> <summary><strong>🔧 Step 4: Update Nginx Configuration</strong></summary>
Update the Nginx configuration file as necessary for your setup (e.g., /etc/nginx/sites-available/default).

</details> <details> <summary><strong>⚡ Step 5: Start Backend Application</strong></summary>
Navigate to the backend directory and start the application using PM2:

    pm2 start server.js

</details> <details> <summary><strong>🚀 Step 6: Start Frontend Application</strong></summary>
Navigate to the frontend directory and start the application using PM2:

    cd frontend
    pm2 start npm --name "react-writebing" -- start
</details>

Pushing Updates to Production
<details> <summary><strong>🔑 Step 1: Login to Azure VM</strong></summary>
Log into the Azure VM using SSH. Replace the placeholders with your actual SSH key and IP address:

    ssh -i <your-key-file.pem> azureuser@<your-vm-ip>

</details> <details> <summary><strong>📂 Step 2: Navigate to Project Directory</strong></summary>
Go to the project directory:

    cd <your-project-directory>

</details> <details> <summary><strong>🔄 Step 3: Pull Latest Changes from GitHub</strong></summary>
Pull the latest changes from the repository:
   
    git pull

</details> <details> <summary><strong>⚙️ Step 4: Rebuild Frontend (If Necessary)</strong></summary>
If changes are made in the frontend, navigate to the frontend directory and run:
   
    cd frontend
    npm run build

</details> <details> <summary><strong>📊 Step 5: Check Application Status</strong></summary>
Ensure that the backend and frontend processes are running in the background using PM2:

    pm2 status
    pm2 monit
    pm2 logs
</details>

Now you are all set! You can easily deploy and update your application using this guide.

Notes
Ensure that you replace all placeholders (<your-vm-ip>, <your-key-file.pem>, <repository-url>, etc.) with your actual credentials.
For troubleshooting, always check the PM2 logs and Nginx error logs.
