# Create CodePipeline

CodePipelines orchestrate the CI and CD processes.

1. From the CodePipeline Console click `Create pipeline`
2. Name the pipeline `devops-bootcamp`.
3. Select `AWS CodeCommit` for `Source provider`.
4. Select `devops-bootcamp` for `Repository name` and `main` for `Branch name`.'
5. Under `Add build stage` select `AWS CodeBuild`.
6. Select `devops-bootcamp` for the `Build project`.
7. Under `Add deploy stage` select `AWS CodeDeploy`.
8. Select `devops-bootcamp` for `Application name` and `Deployment group`.