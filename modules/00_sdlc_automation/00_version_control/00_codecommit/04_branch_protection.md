# Restrict branches with IAM

## Create restricted access group
1. From the IAM console click `Create Policy`
2. Select the `JSON` tab and paste the following code

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "codecommit:Get*",
        "codecommit:GitPull"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "codecommit:GitPush",
        "codecommit:DeleteBranch",
        "codecommit:Merge*"
      ],
      "NotResource": [
        "arn:aws:codecommit:*:*:devops-bootcamp"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "codecommit:GitPush",
        "codecommit:DeleteBranch",
        "codecommit:Merge*"
      ],
      "Resource": [
        "arn:aws:codecommit:*:*:devops-bootcamp"
      ],
      "Condition": {
        "StringNotEquals": {
          "codecommit:References": [
            "refs/heads/main"
          ]
        }
      }
    }
  ]
}
```
3. Name the policy `CodeCommitDevAcces`
4. Add the description `Allow developers to push to branches other than main.`
5. From the IAM console select `User Groups` and click `Create User Group`
6. Name the group dev.
7. Under attach permission policies select `CodeCommitDevAcces`
8. Click `Create User Group`

## Create full access group
1. Create another policy named `CodeCommitCodeOwners` with this JSON
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "codecommit:GitPush",
        "codecommit:DeleteBranch",
        "codecommit:Merge*"
      ],
      "Resource": [
        "arn:aws:codecommit:*:*:devops-bootcamp",
      ]
    }
  ]
}
```
2. Create another group named `code-owners` and attach the policy from step 1.

<img src="assets/branch_protection.gif"
     alt="Branch Protection"
     style="float: left; margin-right: 10px;" />

## References
https://docs.amazonaws.cn/en_us/codecommit/latest/userguide/how-to-conditional-branch.html
https://docs.aws.amazon.com/service-authorization/latest/reference/list_awscodecommit.html