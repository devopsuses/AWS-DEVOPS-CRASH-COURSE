# Create Codebuild Project

1. From the CodeBuild console click `Create Build Project`.
2. Name the project `devops-bootcamp`.
3. From the source paes select `CodeCommit` as the source provider.
4. Select `devops-bootcamp` as the repository.
5. Select reference type Branch and select `main` as the branch.
6. In the Environment panel select `Managed Image`.
7. Select `Ubuntu` for the operating system.
8. In the runtime(s) box select `Stadard`.
9. Under Image select `aws/codebuild/standard:5.0`
10. Leave `New Service Role` selected and accept the default name.
11. Ignore the rest of the settings and click `Create Build Project`.
