## Deploy react WebApp (Yolo) to K8S

## Implementation plan

 ## prerequisites 
  1. Docker Desktop installed
  2. Minikube installed and runing in docker desktop
## Step 1
 Build you 2 images i.e. backend and client images and push them to docker-hub.
## Step 2 
Create you deployment files for both the backend and client 
## Step 3
Create 2 services for both the backend and client services
## Step 4
Create a secret file to hold you mongodb url -> if using a remote connection
if you are using a deployed on in K8S create the Deployment, service and add secrets for mongo username and password 
For may case i faced authentication errors with k8s deployed mongoDB and opted to use the remote connection.
## Step 5
Deploy the file using below command
`
kubectl apply -f <filename>
`
in below order

1. secrets file
2. Deployment files
3. Service files

## Step 6

So that you can be able to access the service you will need to port forward for both the the backend and client services

For backend use below command
`
kubectl port-forward service/yolo-backend-service 5050:5050

`
For client to be able to access the client service in your browser

`
kubectl port-forward service/frontend-service 3000:3000

`

Challenge faced -- for the client app. I tried to store the base url of the backend service to be used in the client app but faced a dependecy issue since the Yolo app was build with a previos version of react that may not support env variables and might required extra configs.

## Step 7

Access the client app using [url](http://localhost:3000) and you can add, edit, delete and view the products.






