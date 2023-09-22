### Steps to do for setting up the application

- Install argoCD
- Make sure the kubectl is configured
- While setting up the application perform these steps
- configure the secrets frist from env file.
- Then create an application
- create a pod.env file
- `kubectl create secret generic astuto-secret -n astuto --from-env-file=./pod.env --dry-run=client -o yaml > secrets.yaml`
- create a namespace `astuto`
- Create credentials template with proper details. This will help to avoid multiple credntials.
-
- creating application in the argocd
-

### Setup Argo cd

```
# create a namespcae
kubectl create namespace argocd

# install argocd. Not production level
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml

# expose the server to load balancer.
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

# expose the password to login from UI.
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
