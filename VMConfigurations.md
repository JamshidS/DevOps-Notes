# Install Java on your Amazon Linux instance
To install Java on your Amazon Linux instance, you first need to connect to your EC2 instance. There are several ways to do this, one of which is by using an SSH client. Here's a detailed guide on how to achieve this:

1. **Connect to Your EC2 Instance**:
   - Open your preferred SSH client. If you're using a Unix-like system (such as Linux or macOS), you can simply open a terminal window.
   - Run this command to switch to the root user
     ```
       sudo su
     ```
   - Copy the SSH command provided by Amazon for connecting to your EC2 instance. This command typically looks like:
     ```
     ssh -i your-key.pem ec2-user@your-ec2-instance-public-ip
     ```
   - Paste this command into your terminal and press Enter. Replace `your-key.pem` with the path to your private key file, and `your-ec2-instance-public-ip` with the public IP address of your EC2 instance.

2. **Install Java**:
   Once you've successfully connected to your EC2 instance via SSH, you can proceed to install Java. Run the following command in your terminal:
   ```shell
   sudo yum install java-17-amazon-corretto -y
   ```
   Let's break down this command:
   - `sudo`: This command is used to run subsequent commands with administrative privileges.
   - `yum`: This is the package manager used by Amazon Linux.
   - `install`: This command tells `yum` to install the specified package.
   - `java-17-amazon-corretto`: This is the package name for Java 17 provided by Amazon Corretto, which is a no-cost, multiplatform, production-ready distribution of the Open Java Development Kit (OpenJDK).
   - `-y`: This option automatically answers "yes" to any prompts that `yum` may display during the installation process, allowing the installation to proceed without requiring manual confirmation.

By running this command, you'll install Java 17 on your Amazon Linux instance. After the installation is complete, you can verify the installation by running `java -version` in your terminal to confirm that Java is installed and the correct version is displayed.
