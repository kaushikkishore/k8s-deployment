## Web application deployment process

You need to run the below command to create a secrets yaml file. This file will change sometimes. Check with the dev team to get understanding of the env file. Inform dev if they are making changes then this need to be updated also.

### Create a namespace

`kubectl create ns astuto`

### Update the secrets file

```
kubectl create secret generic astuto-secret --from-env-file=pod.env -o yaml --dry-run=client > secrets.yaml
```

### update correct version of the deployemnt

Update the deployment to the correct version. Need to think on the process whether the pods yaml will be separate from the deployment or not?

### Create services wisely

Update the services as `LoadBalancer` in case when the application is exposed to public. If the service is used internally then use `ClusterIP`.

### Future

Include helm chart here so in case if you need to configure the changes the values can be configured in the `values.yaml` file and rest can follow along
