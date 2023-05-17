# Cloudformation templates can also be deployed with CodePipelines.

1. Browse to the CodePipeline created previously and click `Edit`.
2. Beneath the `Build` stage click `+Add stage`. Name the stage `Infrastructure`.
3. Click `Add action group`.
4. Set `Action name` to `deploy-cloudformation`.
5. Set `Action provider` to `AWS Cloudformation`.
6. Choose `Source artifact` for `Input artifacts`.
7. Choose `Create or update stack`.
8. Enter `devops-bootcamp-ec2` for `Stack name`.
9. For the tamplate select `Source artifact` and enter the path `deployments/platformdeployment/AWS/EC2/yelb-cloudformation-EC2.yaml`
10. Select a role for `Role name`.
11. Click `Done`.