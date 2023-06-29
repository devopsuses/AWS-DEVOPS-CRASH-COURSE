# Deploy to Auto Scaling Group

1. From the EC2 console select `Autoscaling group / Create Autoscaling group`.
2. Enter `devops-bootcamp` for the name.
3. Select the Launch template created in the previous example. Click `Next`
4. Select the default VPC and all available subnets. Click `Skip to review`.
5. Under `Configure advanced options` click `Edit`.
6. Select `Attach to a new load balancer`.
7. Choose `Internet facing`.
8. Select `Create a target group`. Click `Skip to review`.
