## Coffee Supplier Application Docker Migration

### Introduction
This repository contains the steps and files necessary to migrate the Coffee Supplier Application from a traditional setup to Docker containers. The migration includes containerizing both the Node.js application and the MySQL database, as well as pushing the Docker images to Amazon Elastic Container Registry (Amazon ECR) for future deployment.

### Prerequisites
- AWS Cloud9 IDE
- Docker installed on the AWS Cloud9 EC2 instance
- Access to AWS Management Console

### Steps for Migration

#### Task 3: Migrating the Application to a Docker Container
1. **Create a Working Directory and Move Source Code**
   - Create a directory named `containers` in the AWS Cloud9 IDE.
   - Inside the `containers` directory, create another directory named `node_app` and move the source code into it.

2. **Create a Dockerfile**
   - Inside the `node_app` directory, create a new file named `Dockerfile`.
   - Copy the Dockerfile content from the provided instructions into the `Dockerfile`.

3. **Build Docker Image**
   - Open the terminal in AWS Cloud9 and run the command `docker build --tag node_app .` to build the Docker image.

4. **Verify Docker Image**
   - Run `docker images` to verify that the `node_app` Docker image was created successfully.

5. **Create and Run Docker Container**
   - Run `docker run -d --name node_app_1 -p 3000:3000 node_app` to create and run a Docker container based on the Docker image.

6. **Adjust Security Group**
   - Update the security group of the AWS Cloud9 EC2 instance to allow network traffic on port 3000.

7. **Test Application**
   - Access the web interface of the application running in the Docker container to verify functionality.

#### Task 4: Migrating the MySQL Database to a Docker Container
1. **Create mysqldump File**
   - Dump the data from the MySQL database into a file named `my_sql.sql`.

2. **Create Dockerfile for MySQL**
   - Create a directory named `mysql` and a Dockerfile inside it.
   - Copy the Dockerfile content from the provided instructions into the `Dockerfile`.

3. **Build MySQL Docker Image**
   - Build the Docker image using the command `docker build --tag mysql_server .`.

4. **Verify MySQL Docker Image**
   - Run `docker images` to verify that the `mysql_server` Docker image was created successfully.

5. **Create and Run MySQL Docker Container**
   - Run `docker run --name mysql_1 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=rootpw -d mysql_server` to create and run a MySQL Docker container.

6. **Import Data into MySQL Database**
   - Import the data from the `my_sql.sql` file into the MySQL database running in the Docker container.

#### Task 5: Testing MySQL Container with Node Application
1. **Stop and Remove Node Application Container**
   - Stop and remove the existing node application container.

2. **Discover Network Connectivity**
   - Find the IPv4 address of the MySQL container on the network.

3. **Start New Node Application Container**
   - Run a new node application container with the correct environment variable for database connectivity.

4. **Test Application**
   - Access the web application running in the new Docker container and verify database connectivity.

#### Task 6: Adding Docker Images to Amazon ECR
1. **Authorize Docker Client**
   - Authorize the Docker client to connect to Amazon ECR.

2. **Create Repository**
   - Create a repository in Amazon ECR for the node application Docker image.

3. **Tag and Push Docker Image**
   - Tag the Docker image with the repository URL and push it to Amazon ECR.

### Conclusion
This repository provides a complete guide and necessary files for migrating the Coffee Supplier Application to Docker containers, including the application and MySQL database. The Docker images are pushed to Amazon ECR for future deployment, ensuring scalability and portability of the application.

🚀 Happy Dockerizing! 🐳
