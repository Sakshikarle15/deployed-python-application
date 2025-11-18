# __Deployment of Python Application with Proxy Server__
## Introduction
This project serves as a step-by-step guide for deploying a Python application in a production environment with a proxy server.
It explains how to set up the server, configure the application, install dependencies, and integrate a proxy (such as Nginx) to manage and route incoming traffic efficiently.
By following this deployment process, you can ensure better performance, scalability, and security for your Python-based application.

## Features
* Production-Ready – Runs smoothly in production

* Secure & Efficient – Proxy integration improves performance and security

* Environment Management – Supports virtual environments

## Prerequisites
* Python 3.x – Required to run the application.

* Pip – To install dependencies.

* Git (optional) – For cloning the repository.

* Virtual Environment (venv) – Recommended for isolated setups.

* Proxy Server (Nginx/Apache) – For handling and routing requests in production.

Deployment Steps

Step 1: Launch an EC2 Instance
![wel](./img/pythonapp.png)

Step 2: Copy SSH Command and Paste Command in Git bash
![wel](./img/ssh%20py.png)

Step 3: Update Packages and Install Python3 and pip

  #Update 
      
      sudo yum update
  #Install python3  

      sudo yum install python3 -y 
  #Install pip

       sudo yum install python3-pip

![wel](./img/update%20py.png)          
Step 4: Upload / Clone Your 
Application

1.Install git

       sudo yum install git -y


![wel](./img/install%20git.py.png)     
2. Clone the Application and go inside the pythonapp folder

        # Clone git application
        git clone <git url> 
        # Go inside pythonapp folder
        cd pythonapp/

![wel](./img/gitclone.py.png) 

Step 5: Create and Activate Virtual Environment
    
      # Create virtual environment
      sudo python3 -m venv myenv
      # Activate file 
      sudo bash myenv/bin/activate
 ![wel](./img/virtualenv.png)
Step 6: Install Dependency

     sudo pip install -r requirement.txt  
  ![wel](./img/depen.py.png)   
Step 7: Run the Application at Background

    gunicorn --bind 0.0.0.0:5000 app:app --daemon
 ![wel](./img/gunicorn.png)   

 Step 8: Create a Proxy Server
 
 1. Configure Nginx a Proxy
  
        sudo yum install nginx -y
![wel](./img/nginx.py.png) 
2. Create Server block for your app

* Open nginx.conf file

      cd/etc/nginx
      sudo vim nginx.conf
 ![wel](./img/etcnginx.py.png)     

 3. Edit Server Block

 ![wel](./img/serv.py.png)

 4. Restart Nginx
  
        sudo systemctl restart nginx
 ![wel](./img/re.py.png)  

 5. Allow Port 5000 (to access the python app) in Security Group(AWS EC2) 

  Go to EC2 -> Security Groups -> Edit Inbound Rules

![wel](./img/5000.png)

 Step 9: Test the Deployment

  Copy the public IP of your EC2/Server and paste in into any browser
  
  ![wel](./img/op.py.png)

  ### Summary:
  This project explains how to deploy a Python application in a production environment, including setting up the environment, installing dependency,configuring the app, and using Nginx as a proxy for efficient traffic management.


