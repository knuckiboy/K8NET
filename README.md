# README #

This README would normally document whatever steps are necessary to get your application up and running.

### What is this repository for? ###

* Quick summary
* Version
* [Learn Markdown](https://bitbucket.org/tutorials/markdowndemo)

### How do I get set up? ###

1. Build Docker Image
<br/>
 `docker build -t k8net -f k8Web/Dockerfile .`

2.  Login and publish to DockerHub
<br/>
`docker login`
<br/>
`docker tag k8net knuckiboy/k8net:latest`
Push image to DockerHub
<br/>
`docker push knuckiboy/k8net:latest`

3. Apply kubernetes deployment.yaml 
<br/>
`kubectl apply -f deployment.yaml`

4. Apply kubernetes service.yaml 
<br/>
`kubectl apply -f service.yaml

5. Inspect services
<br/>
`kubectl describe service k8net-web-service`
<br/>
`kubectl get services`
<br/>
`kubectl get deployments`

### Starting of MiniKube ###
1. Starting of minikube & dashboard
<br/>
`minikube start`
<br/>
`minikube dashboard`

2. Create minikube service tunnel for NodePort
<br/>
`minikube service k8net-web-service --url
`

### Contribution guidelines ###

* Writing tests
* Code review
* Other guidelines

### Who do I talk to? ###

* Repo owner or admin
* Other community or team contact