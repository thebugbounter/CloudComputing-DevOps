To run a Python program on Jenkins using the Jenkins workspace, you'll ensure that Jenkins can access and execute Python scripts stored within its workspace directory. Here’s a step-by-step guide on how to achieve this:

### Prerequisites
- Jenkins installed and running on your local machine or server.
- Python installed on the machine where Jenkins is running.
- Basic knowledge of Jenkins job creation and configuration.

### Step-by-Step Guide

#### 1. Create a New Jenkins Job

1. From the Jenkins dashboard, click on `New Item`.
2. Enter a name for your job (e.g., `Python-Script-Job`).
3. Select `Freestyle project` and click `OK`.

#### 2. Configure Source Code Management (Optional)

If your Python script is part of a version-controlled repository (e.g., Git), you can configure Jenkins to check out the code into its workspace:

1. In the job configuration page, scroll down to the `Source Code Management` section.
2. Select your Version Control System (e.g., Git).
3. Enter the repository URL and credentials if it's a private repository.
4. Specify the branch or leave it blank for the default branch.

#### 3. Configure Build Steps

1. Scroll down to the `Build` section.
2. Click on `Add build step` and select `Execute Windows batch command` (for Windows) or `Execute shell` (for Unix-based systems).

   For Windows:
   ```batch
   cd %WORKSPACE%
   python path/to/your/script.py
   ```

   For Unix-based systems:
   ```sh
   cd $WORKSPACE
   python path/to/your/script.py
   ```

   Replace `path/to/your/script.py` with the relative path from the workspace root to your Python script.

   **Explanation**:
   - `%WORKSPACE%` (Windows) or `$WORKSPACE` (Unix) is an environment variable that Jenkins sets to the current job's workspace directory.
   - The `cd` command changes the current directory to the workspace directory where Jenkins checks out the project.

#### 4. Save and Build the Job

1. Click on `Save` to save the job configuration.
2. To build the job manually, click on `Build Now` in the left sidebar.
3. Jenkins will execute the Python script as part of the build process using the Python interpreter installed on the Jenkins server.

### Additional Considerations

- **Python Environment**: Ensure that Jenkins can find the `python` executable in its environment path. You may need to specify the full path to the `python` executable if it's not available globally.
  
- **Workspace Cleanup**: Optionally, you can configure Jenkins to clean up the workspace before each build to ensure a clean environment.

#### Example Python Script Execution

Assuming your Python script `script.py` is located in the root of your repository:

For Windows:
```batch
cd %WORKSPACE%
python script.py
```

For Unix-based systems:
```sh
cd $WORKSPACE
python script.py
```

### Conclusion

You have successfully configured Jenkins to execute a Python script located in its workspace directory. Jenkins will automatically manage the workspace, check out the project (if configured), and execute the Python script as part of the build process.
