# Docker Compose on AWS EC2 Instance with Ubuntu
How to install docker and docker compose on aws ec2 instance with ubuntu
---

## Prerequisites:

- Before you begin, make sure you have the following:

1. An AWS account.

2. An AWS EC2 instance running Ubuntu.

3. SSH access to your EC2 instance.

4. Basic knowledge of Linux commands.


## Step 1: Connect to Your EC2 Instance
```shell
ssh -i your-key.pem ubuntu@your-ec2-ip
```
Replace your-key.pem with your SSH key and your-ec2-ip with your EC2 instance's public IP address.

## Step 2: Update Package Lists
Update the package lists to ensure you have the latest information about available packages:
```shell
sudo apt update
```

## Step 3: Install Docker
Install Docker on your EC2 instance by running the following commands:
```shell
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

## Step 4: Install Docker Compose
Docker Compose is not included in the default Ubuntu repositories, so you'll need to download it separately. Use the following commands to install Docker Compose:
```shell
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## Step 5: Verify Docker Compose Installation
To ensure Docker Compose was installed successfully, check its version:
```shell
docker-compose --version
```
You should see the version information displayed in the terminal.

## Step 6: Create a Docker Compose File
Now, let's create a docker-compose.yml file to define your multi-container application. Here's a basic example:
```shell
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  app:
    image: your-app-image:latest

```
Replace your-app-image with the image name of your application.

## Step 7: Start Your Application
In the directory where your docker-compose.yml file is located, run the following command to start your application:
```shell
docker-compose up -d
```
The -d flag runs the containers in detached mode. you can remove it also

## Step 8: Access Your Application
You can now access your application by navigating to your EC2 instance's public IP address in a web browser.


