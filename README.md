# k8s deployment process 

## Plan 

Cosidering the application container multiple containers. Plan is to create a multi container application where each container will be considered as a single pod. 

Requirements 
- Create a `redis` service (`ClusterIp`)
    - could be running multi node (Need to decide on whether this will be in memory or will use the `AWS EBS`)
- Create a `MySQL` service (`ClusterIP`)
    - Create `AWS EBS volume` and use so the data will be persistance.
- These will be pulled using the `Helm Chart`
- Configure `AWS` `EBS` volume for the storage
- Now create a web application which will connect to the these databases and run some simple crud application 
- create a proper `Helm charts` so you will end up a `PhoenixServer`
- Next step is automate this whole process using the `ArgoCD` pipeline process. 
- 

Persistent storage for Kubernetes 
[AWS Document](https://aws.amazon.com/blogs/storage/persistent-storage-for-kubernetes/)

some handy commands 

start minikube mac os 
`minikube start --driver=qemu --network=socket_vmnet`