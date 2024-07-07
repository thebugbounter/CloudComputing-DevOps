### Configuring Jenkins on AWS EC2 Instance
---
## Introduction to Jenkins
### What is Jenkins?
Jenkins is an open-source automation server that facilitates continuous integration (CI) and continuous delivery (CD). It helps automate the parts of software development related to building, testing, and deploying, allowing for the integration of changes to projects continuously.

### Why Use Jenkins?
- **Continuous Integration**: Jenkins allows developers to frequently commit code changes to a shared repository, automatically triggering builds and tests, ensuring that errors are detected early.
- **Continuous Delivery**: Jenkins automates the deployment process, making it easy to deploy applications to different environments once they are built and tested.
- **Extensibility**: Jenkins supports thousands of plugins that integrate with various development, testing, and deployment tools, making it highly customizable.

## Prerequisites
Before starting, ensure you have:
- An Ubuntu server (version 22.04) with SSH access.
- AWS EC2 instance with the necessary security group settings.

## Steps to Configure Jenkins

### 1. Update the Ubuntu Package Lists
Updating the package lists ensures that you have the latest information about available packages and their dependencies.

```bash
sudo apt update
```

### 2. Install Java Development Kit (JDK 11)
Jenkins requires Java to run. We'll install OpenJDK 11, an open-source implementation of the Java Platform.

```bash
sudo apt install openjdk-11-jdk
```

To verify the installation, check the Java version:

```bash
java -version
```

You should see an output indicating that Java 11 is installed.

### 3. Install Jenkins
Jenkins is not included in the default Ubuntu repositories, so we need to add its repository and key, then install it.

#### a. Add the Jenkins repository key:

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
```

#### b. Add the Jenkins repository:

```bash
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

#### c. Update the package lists:

```bash
sudo apt update
```

#### d. Install Jenkins:

```bash
sudo apt install jenkins
```

### 4. Start and Enable Jenkins Service
Start the Jenkins service and configure it to start on boot:

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

To check the status of Jenkins:

```bash
sudo systemctl status jenkins
```

You should see output indicating that Jenkins is active and running.

### 5. Configure Firewall for Jenkins
By default, Jenkins runs on port 8080. To ensure Jenkins can be accessed, we need to allow traffic on this port.

#### a. Allow traffic on port 8080:

```bash
sudo ufw allow 8080
```

#### b. Allow SSH traffic:

```bash
sudo ufw allow OpenSSH
```

#### c. Enable the firewall:

```bash
sudo ufw enable
```

#### d. Verify the firewall status:

```bash
sudo ufw status
```

Ensure that port 8080 and SSH are listed as allowed.

### 6. Configure AWS Security Groups
In your AWS Management Console, ensure that the security group associated with your EC2 instance allows inbound traffic on the following ports:
- **8080**: For Jenkins
- **80**: For HTTP
- **443**: For HTTPS

### 7. Access Jenkins
Open your web browser and navigate to:

```
http://<your-ec2-instance-public-ip>:8080
```

You will see the Jenkins setup screen. Follow the on-screen instructions to complete the setup.

### Initial Setup
When you first access Jenkins, you will be prompted to unlock Jenkins using the initial admin password. You can find this password by running the following command:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the password displayed and paste it into the setup screen to proceed.

## Conclusion
You've successfully installed and configured Jenkins on an AWS EC2 instance running Ubuntu. Jenkins is now ready to be used for continuous integration and continuous delivery tasks. You can further customize Jenkins by installing plugins and configuring build jobs according to your project's needs.

---

