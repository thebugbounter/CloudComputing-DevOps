
### Step 1: Sign in to AWS Management Console

1. **Go to the AWS Management Console**: Open your web browser and navigate to [AWS Management Console](https://aws.amazon.com/console/).

2. **Log in**: Log in with your AWS credentials. If you don’t have an account, create one by following the sign-up process.

### Step 2: Navigate to EC2 Dashboard

1. **Search for EC2**: In the AWS Management Console, use the search bar at the top to search for "EC2" and select it.

2. **Open EC2 Dashboard**: This will take you to the EC2 Dashboard, where you can manage your instances.

### Step 3: Launch an EC2 Instance

1. **Click "Launch Instance"**: On the EC2 Dashboard, click the "Launch Instance" button to start the process of creating a new VM.

2. **Choose an Amazon Machine Image (AMI)**: Select an AMI from the list. For this example, choose "Amazon Linux, SSD Volume Type" which is free-tier eligible.

3. **Choose an Instance Type**: Select the instance type. For the free tier, choose "t2.micro".

4. **Configure Instance Details**: You can leave the default settings for this demonstration, which is sufficient for a basic setup. Click "Next: Add Storage".

5. **Add Storage**: The default storage size is usually sufficient. For this example, you can leave the default settings. Click "Next: Add Tags".

6. **Add Tags**: Optionally, you can add tags to your instance. This is useful for identifying your instances later. Click "Next: Configure Security Group".

7. **Configure Security Group**: Create a new security group or use an existing one. Make sure to allow SSH traffic:
   - Type: SSH
   - Protocol: TCP
   - Port Range: 22
   - Source: Anywhere (0.0.0.0/0) (For production use, restrict the source to your IP for security)
   
   Click "Review and Launch".

8. **Review Instance Launch**: Review your settings. Click "Launch".

9. **Select a Key Pair**: Choose an existing key pair or create a new one. This key pair is used to securely connect to your instance. Download the key pair file (.pem) and keep it safe.

10. **Launch Instance**: Click "Launch Instances". Your instance will start launching.

### Step 4: Connect to Your EC2 Instance

1. **View Instances**: Go back to the EC2 Dashboard and click on "Instances" in the left-hand menu. You should see your newly launched instance.

2. **Get Public DNS**: Wait until the instance state is "running" and the status checks are passed. Select your instance and note down the Public DNS (IPv4) address.

3. **Open EC2 Instance Connect**: In the EC2 Console, select your instance, click on "Connect" and use "EC2 Instance Connect" to access your instance directly from the AWS console.

### Step 5: Verify Connection

1. Once connected, you should see a welcome message from the Amazon Linux AMI. You now have command-line access to your EC2 instance.

### Step 6: Install a Web Server

1. **Update the package index**:
   ```bash
   sudo yum update -y
   ```

2. **Install Apache web server**:
   ```bash
   sudo yum install -y httpd
   ```

3. **Start the Apache service**:
   ```bash
   sudo service httpd start
   ```

4. **Enable the Apache service to start on boot**:
   ```bash
   sudo systemctl enable httpd
   ```

### Step 7: Deploy Your Website

1. **Install Git**:
   ```bash
   sudo yum install -y git
   ```

2. **Clone your GitHub repository**:
   ```bash
   git clone https://github.com/thebugbounter/preet-watches.git /var/www/html/
   ```

3. **Adjust ownership and permissions**:
   ```bash
   sudo chown -R apache:apache /var/www/html
   sudo chmod -R 755 /var/www/html
   ```

### Step 8: Access Your Web Server

 **Open your web browser**: Go to the public DNS address of your instance. You should see the content of your website deployed from the GitHub repository.

