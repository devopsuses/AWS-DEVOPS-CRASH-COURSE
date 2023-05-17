# Parameterize the template

1. From the `devops-bootcamp-ec2` stack select `Stack actions / Create change set for current stack`
2. Select `Edit template in designer`.
3. Add a `LaunchTemplateVersion` parameter:
```yaml
Parameters:
    LaunchTemplateVersion:
        Description: Version of the launch template to use.
        Type: String
```
4. Set a reference:
```yaml
Properties:
      LaunchTemplate:
        LaunchTemplateName: devops-bootcamp
        Version: !Ref LaunchTemplateVersion
```