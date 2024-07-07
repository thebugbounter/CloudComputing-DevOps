

# Running Jenkins on Localhost (Windows)
---

## Introduction to Jenkins

### What is Jenkins?
Jenkins is an open-source automation server that facilitates continuous integration (CI) and continuous delivery (CD). It automates parts of the software development process related to building, testing, and deploying, allowing for frequent integration of changes.

### Why Use Jenkins?
- **Continuous Integration**: Jenkins automates the process of merging code changes frequently, running builds, and tests, ensuring early detection of errors.
- **Continuous Delivery**: Jenkins automates the deployment process, enabling the continuous release of software.
- **Extensibility**: Jenkins supports thousands of plugins that integrate with various development, testing, and deployment tools, making it highly customizable.

## Prerequisites
- A Windows PC with administrative privileges.
- Java Development Kit (JDK) installed.

## Steps to Install and Run Jenkins

### 1. Install Java Development Kit (JDK)

Jenkins requires Java to run. You can download and install the latest JDK from the [Oracle website](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
#### a. Download and Install JDK
1. Go to the Oracle JDK download page.
2. Download the installer for your Windows version.
3. Run the installer and follow the installation instructions.
4. Set the `JAVA_HOME` environment variable:
    - Open the Start Menu, search for "Environment Variables", and select "Edit the system environment variables".
    - In the System Properties window, click on the "Environment Variables" button.
    - Under System variables, click "New" and add `JAVA_HOME` with the path to your JDK installation directory (e.g., `C:\Program Files\Java\jdk-11.0.11`).

#### b. Verify Java Installation
Open a Command Prompt and run:

```cmd
java -version
```

You should see the version of Java installed.

### 2. Download and Install Jenkins

#### a. Download Jenkins
1. Visit the Jenkins download page: [Jenkins Download](https://www.jenkins.io/download/).
2. Under the "Windows" section, download the "Windows Installer" (Jenkins.msi).

#### b. Install Jenkins
1. Run the Jenkins.msi installer.
2. Follow the installation instructions.
3. By default, Jenkins will be installed in `C:\Program Files (x86)\Jenkins`.

### 3. Start Jenkins
1. Jenkins runs as a Windows service by default.
2. To start Jenkins, open the Services application (search for "Services" in the Start Menu).
3. Find "Jenkins" in the list, right-click, and select "Start".

### 4. Configure Jenkins

#### a. Initial Setup
1. Open a web browser and navigate to `http://localhost:8080`.
2. You will be prompted to unlock Jenkins using the initial admin password.
3. To find the password, open the file located at `C:\Program Files (x86)\Jenkins\secrets\initialAdminPassword` and copy the password.
4. Paste the password into the setup screen and click "Continue".

#### b. Customize Jenkins
1. Select "Install suggested plugins" to install the recommended set of plugins.
2. Jenkins will start installing the selected plugins.

#### c. Create Admin User
1. After the plugins are installed, you will be prompted to create the first admin user.
2. Fill out the form with your desired username, password, and other details.
3. Click "Save and Finish".

#### d. Jenkins is Ready
1. You should now see the Jenkins dashboard.
2. Jenkins is now ready to use. You can start creating and configuring jobs to automate your development workflows.
