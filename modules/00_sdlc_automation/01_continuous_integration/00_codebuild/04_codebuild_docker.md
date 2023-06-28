# Build Docker images

Codebuild can build images and push them to repositories, however it doesn't have an integration with ECR.

1. Create an ECR repository.
2. Name it `yelb-appserver`.
3. Click `Create repository`.
4. Create a new `Build project`.
5. Create an environment variable `AWS_ACCOUNT_ID=<your AWS account ID>`
6. Update the service role permission policy to allow access to the repository.
```json
{
  "Statement": [
    {
      "Action": [
        "ecr:BatchCheckLayerAvailability",
        "ecr:CompleteLayerUpload",
        "ecr:GetAuthorizationToken",
        "ecr:InitiateLayerUpload",
        "ecr:PutImage",
        "ecr:UploadLayerPart"
      ],
      "Resource": "*",
      "Effect": "Allow"
    },
  ],
  "Version": "2012-10-17"
}
```
7. Set `Priviledged mode` on.
8. Set the buildspec to this:

```yaml
version: 0.2

phases:
  pre_build:
    commands:
      - echo Logging in to Amazon ECR...
      - aws ecr get-login-password --region $AWS_DEFAULT_REGION | docker login --username AWS --password-stdin $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com
  build:
    commands:
      - echo Build started on `date`
      - echo Building the Docker image...
      - docker build -t yelb-appserver:latest yelb-appserver/
      - docker tag yelb-appserver:latest $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/yelb-appserver:latest
  post_build:
    commands:
      - echo Build completed on `date`
      - echo Pushing the Docker image...
      - docker push $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$IMAGE_REPO_NAME:$IMAGE_TAG
```

references:
- https://docs.aws.amazon.com/codebuild/latest/userguide/sample-docker.html
- https://docs.aws.amazon.com/codebuild/latest/userguide/build-env-ref-env-vars.html
