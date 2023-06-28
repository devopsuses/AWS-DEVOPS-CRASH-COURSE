# Automate builds

1. Edit the `EventBridge` rule created in the `CodeCommit` excercise:
2. Edit the Target.
3. Change Target to `CodeBuild project`.
4. Enter the ARN for the `CodeBuild project` (ex. arn:aws:codebuild:us-west-1:202151242785:project/devops-bootcamp)  
> Substitute the ARN for your environment.
> The ARN can be retrived with the command `aws codebuild batch-get-projects --names devops-bootcamp`.
