# Cloudwatch logging on ECS

Some services such as ECS and Lambda have built in support for Cloudwatch logging and don't require an agent to be installed.

1. Modify the Task Definitions in the Yelb CDK deployment to use the `AWS Logs` driver:

```typescript
const yelbuicontainer = yelbuitaskdef.addContainer("yelb-ui-container", {
      image: ecs.ContainerImage.fromRegistry("mreferre/yelb-ui:0.10"),
      environment: {"SEARCH_DOMAIN": yelbnamespace.namespaceName},
      logging: new ecs.AwsLogDriver({ streamPrefix: 'yelb-ui', mode: ecs.AwsLogDriverMode.NON_BLOCKING }),
    })
```
2. Deploy the stack:
```bash
cdk deploy
```

## Add a log generator
Since our application doesn't have any traffic let's generate some logs.

1. Add a new task definition and service:
```typescript
    const logjamtaskdef = new ecs.FargateTaskDefinition(this, "logjam-taskdef", {
      memoryLimitMiB: 2048, // Default is 512
      cpu: 512, // Default is 256
    });

    const logjamcontainer = logjamtaskdef.addContainer("logjam", {
      image: ecs.ContainerImage.fromRegistry("bananalab/logjam:latest"),
      command: ['--delay=0.1'], 
      logging: new ecs.AwsLogDriver({ streamPrefix: 'logjam', mode: ecs.AwsLogDriverMode.NON_BLOCKING}),
    })

    // Create a standard Fargate service 
    const logjamservice = new ecs.FargateService(this, "logjam-service", {
      cluster: yelbcluster, // Required
      serviceName: "logjam",
      taskDefinition: logjamtaskdef,
    });  
```

## Explore the generated logs

1. From the ECS logjam service click logs.  Browse the logs.
2. Click `View in Cloudwatch`
3. Explore the logs here.
