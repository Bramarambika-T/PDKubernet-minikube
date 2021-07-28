# PDKubernet-minikube
Create a NGINX docker container and build :

docker build -t bramarambikatsaliki/nginx:latest dockerfile-location
Push it to docker hub - using docker push bramarambikatsaliki/nginx:latest
If there is login problem- use docker login cmd then docker push bramarambikatsaliki/nginx:latest

if you like to run image - docker run -it -d -p 8080:80 nginx

Minikube cluster Installation in local Mac machine :
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube

Start your cluster :
step 1 : minikube start

step 2 : create the deployment - 
kubectl create deployment nginx --image=bramarambikatsaliki/nginx:latest

Step 3 : expose to node port -
kubectl expose deployment nginx --type=NodePort --port=8080

Step 4 : check the service 
kubectl get services nginx

Step 5 : Launch the service 
minikube service nginx 
kubectl port-forward service/nginx 7080:8080

Step 6 : LoadBalancer deployments
kubectl create deployment balanced --image=bramarambikatsaliki/nginx:latest 
kubectl expose deployment balanced --type=LoadBalancer --port=8080
minikube tunnel
kubectl get services balanced
