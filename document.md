### Steps to do for setting up the application 

- Install argoCD 
- Make sure the kubectl is configured 
- While setting up the application perform these steps 
- configure the secrets frist from env file. 
- Then create an application 
- create a pod.env file
- `kubectl create secret generic my-secret --from-env-file=./pod.env --dry-run=client -o yaml > secrets.yaml`
- create a namespace `astuto`
- Create credentials template with proper details. This will help to avoid multiple credntials. 
- 
- creating application in the argocd 
- 