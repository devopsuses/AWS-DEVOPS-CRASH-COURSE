# Install and configure Cloudwatch Agent.

## Install Cloudwatch agent manually.
1. Connect to an instance with `Cloudwatch session manager` or `SSH`.
2. Run `sudo yum install amazon-cloudwatch-agent`.

## Install Cloudwatch agent with SSM.
1. Open the SSM console and select `Run command`
2. In the `Command document` list, choose `AWS-ConfigureAWSPackage`.
3. In the Name box, enter `AmazonCloudWatchAgent`.
4. In `Target selection` select `Specify instance tags` and enter `app = devops-bootcamp`
5. Under `Output options` select `S3 Bucket` and enter a bucket or create a new bucket.  Enter `cloudwatch-agent-install-output`.

## Configure the Cloudwatch agent.
1. Connect to an instance with `Cloudwatch session manager` or `SSH`.
2. Run `sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard`.
3. Select choices in the CLI wizard and store the result in SSM parameter store.

## Start the Cloudwatch agent.
1. Create another `Run command`.
2. In the `Command document` list choose `AmazonCloudWatch-ManageAgent`.
3. In `Target selection` select `Specify instance tags` and enter `app = devops-bootcamp`.
4. In the `Action` list, choose `configure`.
5. In the `Optional Configuration Source` list, choose `ssm`.
6. In the `Optional Configuration Location` box, enter the name of the agent configuration file that you created and saved to `Systems Manager Parameter Store`.
7. In the `Optional Restart` list, choose `yes` to start the agent after you have finished these steps.
8. Under `Output options` select `S3 Bucket` and enter a bucket or create a new bucket.  Enter `cloudwatch-agent-configure-output`.

# Verify Agent
1. Connect to an instance with `Cloudwatch session manager` or `SSH`.
2. Run `ps aux | grep amazon-cloudwatch-agent`.
3. You should see a cloudwatch agent process running.
4. Verify logs are sent to Cloudwatch in the console.
