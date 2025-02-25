# <p align="">Simple WebServer with Docker
## <p align="">About the project</p>
   This project demonstrates how to create a simple web server with Docker. In this , we create a basic web server application and package it within a Docker container, 
   allowing for easy deployment and management of your web service across different environments by leveraging Docker's containerization features.
   
![image](https://github.com/user-attachments/assets/55d631b4-e981-4d9d-b56f-b8d35c91d788)

## Overview

Create basic web server code that listens on a port and serves a basic HTML page when accessed. 
Write a Dockerfile,specify a base image and copy the web server code into the container.
Build the Docker Image and finally run the container using Docker commands.

## Pre-requisites

* AWS Prerequisites
* Install Docker
* Create a directory
* Create an index file
* Create a Dockerfile
* Build the docker image
* Start the container
* Allow the required port
* Access your web server

## <p align="">Steps</p>

### <p align="">Step1:</p>

1. Set up an EC2 instance in an Amazon VPC by following below images.

![Screenshot 2025-02-23 153719](https://github.com/user-attachments/assets/a7982145-343a-481b-b282-2b565d446a73)

![Screenshot 2025-02-23 153735](https://github.com/user-attachments/assets/c290c7ef-74f7-4e70-8f48-0b51f8169234)

![Screenshot 2025-02-23 153752](https://github.com/user-attachments/assets/f2ababc3-8b04-429c-a2f9-e504a613d559)

![Screenshot 2025-02-23 153837](https://github.com/user-attachments/assets/5225db82-449b-4c3a-a031-c1d59ac9aae1)

2. Finally Launch the EC2 Instance.
3. Connect to the instance through the putty or through any terminal using Key pair.

### <p align="">Step2:</p>

1. After connecting to the instance, Install Docker using the following commands.
2. Before installing Docker, you should update the package index:
   
```bash
sudo yum update -y
```    

3. To install Docker on Amazon Linux, you can use the following command:

 ```bash
sudo yum install docker -y
```

4. After installing Docker, you will need to start the Docker service:

```bash
sudo systemctl start docker
```

5. Once you have started the Docker service, you can verify that it is running by running the following command in your terminal:

```bash
sudo docker run hello-world
```

6. If the installation is successful, you will see a message indicating that Docker is working correctly.
7. To start the Docker service automatically when the instance starts, you can use the following command:

```bash
sudo systemctl enable docker
```

8. Verify the Docker installation by running the Docker version command:

```bash
docker --version
```

### <p align="">Step3:</p>

1. Create a directory for the web server project using below commands

```bash
mkdir nginx_image
cd nginx_image
```

2. Create another directory called Files where we will store the index file and the dockerfile.

```bash
mkdir files
cd files
```

### <p align="">Step4:</p>

Create index file naming as index.html which contains html simple code.

```bash
vim index.html
```

### ![Screenshot 2025-02-25 133436](https://github.com/user-attachments/assets/4b46a5d4-90ff-4a84-a4a3-7ec86334a62a)


