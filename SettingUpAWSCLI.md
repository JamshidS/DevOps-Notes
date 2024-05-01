## Setting up AWS CLI

1. **Install AWS CLI**: Install the AWS Command Line Interface (CLI) on your local machine to interact with AWS services.

2. **Configure AWS CLI**: Run `aws configure` and provide your AWS Access Key ID, Secret Access Key, default region, and output format.

3. **EC2 Instance IAM Role**: Create an IAM role for an EC2 instance to grant access to the S3 bucket for private access.

## Managing S3

### Uploading Files to S3

1. **Using AWS CLI**: Use the `aws s3 cp` command to upload files to an S3 bucket.

   ```bash
   aws s3 cp <local_file_path> s3://<bucket_name>/<destination_path>
   ```

### Downloading Files from S3

1. **Using AWS CLI**: Use the `aws s3 cp` command to download files from an S3 bucket.

   ```bash
   aws s3 cp s3://<bucket_name>/<source_path> <local_destination_path>
   ```

## Deploying Spring Boot Application to EC2

1. **Copy JAR File to EC2**: Use SCP or AWS CLI to copy the Spring Boot application JAR file to your EC2 instance.

2. **Run Application**: SSH into your EC2 instance and run the Spring Boot application using the `java -jar` command.

   ```bash
   java -jar your-application.jar
   ```

3. **Access Application**: Access your application via the public IP address or DNS hostname of your EC2 instance, appending the port number if needed (e.g., `http://example.com:8080`).

## Terminating Processes on EC2

1. **Identify Process ID (PID)**: Use `netstat` or `lsof` to find the PID of the process running on the desired port.

   ```bash
   sudo netstat -tuln | grep <port_number>
   sudo lsof -i :<port_number>
   ```

2. **Terminate Process**: Once you have the PID, use the `kill` command to terminate the process.

   ```bash
   sudo kill <PID>
   ```

3. **Verify Termination**: Check if the process has been successfully terminated using `netstat` or by attempting to access the port.

   ```bash
   sudo netstat -tuln | grep <port_number>
   ```

By following these steps, you can effectively manage S3, deploy Spring Boot applications to EC2, and terminate processes running on your EC2 instance. If you encounter any issues or have further questions, feel free to ask!
