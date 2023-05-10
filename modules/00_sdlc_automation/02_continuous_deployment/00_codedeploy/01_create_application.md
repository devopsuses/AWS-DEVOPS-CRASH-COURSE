# CodeDeploy Applications

## Create CodeDeploy Application

1. From the CodeDeploy console select `Create application`.
2. Name the application `devops-bootcamp`.
3. Select `EC2 / On-premisis`.
4. Click `Create application`.

## Create IAM Role

1. From the IAM console select `Create role`.
2. Slect `AWS service` under `Trusted entity type`
3. Select `CodeDeploy` under `Use cases for other AWS services`.
4. Click `Next` the `Next` again under `add permissions`.
5. Name the role `DevOpsBootcampCodeDeployRole`
6. Click `Create role`.


## Create Deployment Group.

1. From the `devops-bootcamp` console click `Create deployment group`.
2. Enter `devops-bootcamp` for the deployment group name.
3. Select `DevOpsBootcampCodeDeployRole` for the `Service role`.
4. Select `Amazon EC2 instances` under `Environment configuration`.
5. In the `Tag group` field enter `app=devops-bootcamp`.
6. Deselect `Load balancer`.
7. Click `Create deployment group`.

## Create Deployment.

1. From the `devops-bootcamp` console click `Create deployment`.
2. Select `devops-bootcamp` from the `Deployment group` field.
3. In revision location enter the S3 path of the CodeBuild artifact created earlier.
4. Select `.zip` for `Revision file type`.
5. Click `Create deployment`.