# Project Documentation: Deployment of MEAN Stack on EC2 Instance

## Overview

This project is a documentation guide for setting up a MEAN (MongoDb,ExpressJs,Angular.js,NodeJs) stack on an Amazon EC2 instance. The MEAN stack is a popular web development environment that provides the necessary components to run dynamic websites and web applications using Javascript technologies.

### Components

- **MongoDB:** a no-sql database that store data inform of documents
- **ExpressJs:** a serverside web application javascript framework
- **Angular:** a frontend Javascript framework used for UI(user interface) design.
- **NodeJs:** a runtime environment that allows javascript to run on machine instead of browsers.

## Setting up the EC2 Instance

1. **Launch an EC2 Instance**: 
   - Sign in to the AWS Management Console.
   - Navigate to EC2 Dashboard.
   - Click on "Launch Instance" and choose Ubuntu Server 24.04 LTS as the operating system.
![launch instance](image/launch%20instance.png)


2. **Configure Instance Details**:
   - Choose instance type, network, subnet, and other settings as per your requirements.

3. **Add Storage**:
   - Allocate storage space according to your needs.

4. **Add Tags**:
   - Optionally, add tags for better organization.
5. **Configure Security Group**:
   - Create a new security group or use an existing one.
   - Allow inbound traffic on ports 80 (HTTP), 22 (SSH), and 443 (HTTPS) from your IP address
![sg](image/sg.png)

6. **Review and Launch**:
   - Review the configuration and launch the instance.
![instance](image/instance.png)

7. **Connect to the Instance**:
   - Use windows terminal to connect to the instance via SSH.
![instance](image/connect%20instance.png)

8. **SSH to the instance**
```
ssh -i "MEAN.pem" ubuntu@<public DNS>
```
![instance](image/ssh.png)

## Installing MEAN Stack
**In this project we are going to implement a simple book register**
## Step 1: Install nodejs

1. Update and Upgrade Ubuntu
```bash
sudo apt update
sudo apt upgrade
```
![instance](image/ssh1.png)

2. Add certificates and Node.js repository:
```bash
sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates

curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```
![instance](image/ssh2.png)

3. Install nodeJs:

```bash
sudo apt install -y nodejs
```
The above commands will install Node.js and npm (Node Package Manager).

![instance](image/ssh3.png)

---

## Step 2 -  Install MongoDB
1. Download the GPG key for MongoDB:

```bash
 sudo apt-get install -y gnupg curl 
 curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \ sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \ --dearmor
 ```
![instance](image/ssh4.png)

2. Add the MongoDB repository to your system's package sources list:

 ```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
```
![instance](image/ssh5.png)

