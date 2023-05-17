# References

CloudFormation resources can refer to one another.  In this example we create a DNS record that points to our EC2 instance.  Since the DNS record can't be created until the public IP is known it can't be created until the EC2 instance is created. This is an inferred dependency.

```yaml
YelbARecord:
    Type: AWS::Route53::RecordSet
    Properties:
        HostedZoneName: bananalab.com.
        Name: yelb.bananalab.com.
        Type: A
        TTL: '900'
        ResourceRecords:
        - !GetAtt YelbInstance.PublicIp
```