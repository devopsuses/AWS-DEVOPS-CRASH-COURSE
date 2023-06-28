# CodeBuild events

Like most AWS services CodeCommit emits events when the state of the repository changes.

1. From the AWS Console open Amazon Event Bridge.
2. From the laft side menu select Rules, then click Create rule.
3. Create SNS topic named `devops-bootcamp-repo-change`.
4. Create a rule:
     1. Name `devops-bootcamp-repo-change`. Click `Next`.
     2. For `Sample events` select `CodeCommit Repository State Change`.
     3. Under `Event pattern` select `CodeCommit` for the pattern and `CodeCommit Repository State Change` for`Event type`.
     4. Select `Specific resource by ARN` and enter `arn:aws:codecommit:us-east-1:123456789012:devops-bootcamp`.
     5. Click `Next`.
     6. Select the `SNS` topic.
     7. Click `Create rule`.
        
