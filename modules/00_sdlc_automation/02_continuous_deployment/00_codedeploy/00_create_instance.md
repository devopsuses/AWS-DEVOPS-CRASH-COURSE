# Create a target instance for backend deployments

## Create Launch Template
1. Open the EC2 console and select `Launch Templates / Create Template`.
2. Under `Application and OS Images` select `Quick Start / Amazon Linux`.
3. Select `Create Security Group`. Name the security group `devops-bootcamp`.
4. Under `description` enter `Allow HTTP`
5. Under `Inbound security group rules` create a rule to allow port 80 from anywhere. 
6. Under `Resource tags` enter `app=devops-bootcamp`
7. Expand `Advanced Details` and click `Create New IAM profile`

## Create instance role.
1. From the IAM Roles console click `Create Role`
2. Select `Trusted entity type AWS Service`
3. Select `Common use cases = EC2`
4. Click `Add permissions` and these policies: `AmazonSSMManagedInstanceCore`, `AmazonEC2RoleforAWSCodeDeploy`, `CloudWatchAgentServerPolicy`, `CloudWatchLogsFullAccess`, `AmazonS3ReadOnlyAccess`
5. Name the role `DevOpsBootcampInstanceRole`
6. Click `Create Role`

## Finish Launch Template creation.

1. Return to the `Launch Template` creation console.
2. Refresh the list of available instance profiles.
3. Select `DevOpsBootcampInstanceRole`.
4. Click `Create launch template`.

## Create instance
1. From the EC2 Console select `Launch Instance / Launch instance from template`.
2. Select the Launch Template created above.
3. Click `Launch instance`.
