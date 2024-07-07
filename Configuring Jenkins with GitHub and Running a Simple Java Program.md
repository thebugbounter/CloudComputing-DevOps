
## Configuring Jenkins with GitHub and Running a Simple Java Program

### Prerequisites
- Jenkins installed and running on your local machine.
- A GitHub account.
- The GitHub repository URL: `https://github.com/thebugbounter/JenkinsTesting.git`.
- Java installed on your local machine.

### 1. Install Necessary Jenkins Plugins
To integrate Jenkins with GitHub, you need to install a few plugins.

1. Open Jenkins in your web browser: `http://localhost:8080`.
2. Go to `Manage Jenkins` > `Manage Plugins`.
3. Click on the `Available` tab and search for the following plugins:
   - `Git Plugin`
   - `GitHub Integration Plugin`
4. Select the plugins and click on `Install without restart`.

### 2. Create a New Jenkins Job

1. From the Jenkins dashboard, click on `New Item`.
2. Enter a name for your job (e.g., `GitHub-Java-Test`).
3. Select `Freestyle project` and click `OK`.

### 3. Configure Source Code Management

1. In the job configuration page, scroll down to the `Source Code Management` section.
2. Select `Git`.
3. In the `Repository URL` field, enter `https://github.com/thebugbounter/JenkinsTesting.git`.
4. If the repository is private, you need to add your GitHub credentials:
   - Click on `Add` next to `Credentials`.
   - Select `Jenkins` from the dropdown.
   - Click `Add Credentials` and fill in your GitHub username and personal access token (generated from your GitHub account).
   - Select your credentials from the dropdown.

### 4. Configure Build Triggers

1. Scroll down to the `Build Triggers` section.
2. Check the `GitHub hook trigger for GITScm polling` option. This will allow Jenkins to automatically build the project when changes are pushed to the repository.

### 5. Add Build Steps

1. Scroll down to the `Build` section.
2. Click on `Add build step` and select `Execute shell` (for Unix-based systems) or `Execute Windows batch command` (for Windows).
3. Enter the following command to compile and run the Java program:

For Windows:
```batch
javac Hello.java
java Hello
```

For Unix-based systems:
```sh
javac Hello.java
java Hello
```

### 6. Save and Build the Job

1. Click on `Save` to save the job configuration.
2. To build the job manually, click on `Build Now` in the left sidebar.
3. To view the console output, click on the build number in the `Build History` section, and then click on `Console Output`.

### 7. Set Up GitHub Webhook

To automate the build process when changes are pushed to the repository, set up a webhook in GitHub.

1. Go to your GitHub repository: `https://github.com/thebugbounter/JenkinsTesting`.
2. Click on `Settings` > `Webhooks` > `Add webhook`.
3. In the `Payload URL` field, enter `http://<your-jenkins-url>/github-webhook/`. Replace `<your-jenkins-url>` with your Jenkins server URL.
4. Set the `Content type` to `application/json`.
5. Select `Just the push event`.
6. Click `Add webhook`.

### Conclusion

You have successfully configured Jenkins to build a simple Java program from a GitHub repository. Jenkins will now automatically trigger builds when changes are pushed to the repository, and you can view the results in the Jenkins dashboard.
