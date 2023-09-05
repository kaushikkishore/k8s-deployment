to create a secrets 

kubectl create secret generic mysql-secret --from-literal=mysql-root-password=YOUR_ROOT_PASSWORD


to update mysql values 

```
# Set the passwords for MySQL users by referencing the Kubernetes Secret
auth:
  existingSecret: mysql-secret
  rootPasswordKey: mysql-root-password

```

Now create a script which will apply 

```
#!/bin/bash

# Set your desired MySQL root password
MYSQL_ROOT_PASSWORD="YOUR_ROOT_PASSWORD"

# Create a Kubernetes Secret for the MySQL root password
kubectl create secret generic mysql-secret --from-literal=mysql-root-password="$MYSQL_ROOT_PASSWORD"

# Update the MySQL values file
cat <<EOF > mysql-values.yaml
global:
  mysqlRootPassword: ""

auth:
  existingSecret: mysql-secret
  rootPasswordKey: mysql-root-password

# ... (other MySQL configurations as needed)
EOF

# Install MySQL using Helm with the updated values file
helm install my-mysql bitnami/mysql -f mysql-values.yaml

```

Add permission to execute 

`chmod +x deploy-mysql.sh`

Run the code 

`./deploy-mysql.sh`