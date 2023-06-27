# Analyze Yelb ECS deployment.

Availability zones are the basic enabler of resilient services in AWS.  AZs are geographically nearby but have no dependencies on each other.  An AZ spans at least one distinct building and may be several miles from the other AZs in the region.

1. Analyze the network components.
2. Identify the compute platform for resiliancy.
3. Determine the state requirements of the services.
4. Ensure that all stateless services have at least 2 instances across availability zones.
5. Identify load balancing options for stateless services.
6. Analyze requirements and options for stateful services.

* https://aws.amazon.com/dynamodb/faqs/
* https://docs.amazonaws.cn/en_us/AmazonElastiCache/latest/red-ug/AutoFailover.html
* https://aws.amazon.com/rds/ha/