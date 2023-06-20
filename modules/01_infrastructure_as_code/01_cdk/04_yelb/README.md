# Deploy Yelb to ECS using the CDK.

1. Change to the `yelb` project and set the directory to `deployments/platformdeployment/AWS/ECS/cdk`
2. Examine the code in `lib`
3. Run

``` bash
npm install
cdk synth
```

4. Examine the Cloudformation template in cdk.out
5. Deploy stack

```bash
cdk deploy
```
