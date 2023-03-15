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

<img src="assets/branch_protection.gif"
     alt="Branch Protection"
     style="float: left; margin-right: 10px;" />