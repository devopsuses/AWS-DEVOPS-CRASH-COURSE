# Create Codebuild Project

1. From the CodeBuild console click `Create Build Project`.
2. Name the project `devops-bootcamp`.
3. From the source paes select `CodeCommit` as the source provider.
4. Select `devops-bootcamp` as the repository.
5. Select reference type Branch and select `main` as the branch.
6. In the Environment panel select `Managed Image`.
   > [Review which runtimes are available in each managed image.](https://docs.aws.amazon.com/codebuild/latest/userguide/available-runtimes.html)
8. Select `Ubuntu` for the operating system.
9. In the runtime(s) box select `Stadard`.
10. Under Image select `aws/codebuild/standard:5.0`
11. Leave `New Service Role` selected and accept the default name.
12. Select `Insert build commands`.
13. Ignore the rest of the settings and click `Create Build Project`.
