# Artifacts

Artifacts represent the product of the build process.

## Enable artifacts
1. From the `devops-bootcamp` build project select `Edit / Artifacts`
2. Select `Type / S3 Bucket`
3. In the `Bucket Name` field select your bucket (You may need to create a bucket first).
4. In the `Name` field enter `devops-bootcamp`
5. In the `Namespace-type` field select `Build ID`
6. For `Artifacts Packaging` select `Zip`.
7. Leave the rest of the fields default.
8. Run a build and verify artifacts were created.
