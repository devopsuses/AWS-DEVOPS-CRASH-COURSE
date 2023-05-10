# Create Repository

1. Search for CodeCommit in the AWS Console.
2. From the CodeCommit Console select `Create Repository`.
3. In `Repository Name` type `devops-bootcamp`.
4. In the `Description` box enter a helpful description and click `Create`.
5. Clone the example application:

```bash
git clone https://github.com/bananalab/yelb.git
```

6. Set the git remote to your CodeCommit repository and push the sample code:

```bash
cd yelb
git remote set-url origin ssh://git-codecommit.us-west-1.amazonaws.com/v1/repos/devops-bootcamp
git push
```
