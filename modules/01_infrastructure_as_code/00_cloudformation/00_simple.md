# Create an EC2 Instance template.

1. Open the CloudFormation console and click `Create stack`.
2. Select `Create template in Designer`. Click `Next`.
3. In the template designer locate EC2 / Instance and drag it onto the canvas.
4. Set the template language to YAML.
5. Edit `Properties`:
```yaml
Properties:
    LaunchTemplate:
        LaunchTemplateName: devops-bootcamp
        Version: 4
```
>> Note: The template version may be different... you can look it up in the EC2 console.

6. Click `Create stack`
7. Click `Next`
8. Name your stack `devops-bootcamp-ec2`
