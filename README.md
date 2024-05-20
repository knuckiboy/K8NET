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
<br/>
`kubectl describe ingress k8net-ingress --namespace dev`

6. Create kubernetes secrets
<br/>
`kubectl create secret tls k8net-dev-secrets --namespace dev --key openssl/server.key --cert openssl/server.crt`


### Starting of MiniKube ###
1. Starting of minikube & dashboard
<br/>
`minikube start`
<br/>
`minikube dashboard`

2. Create minikube service tunnel for NodePort
<br/>
`minikube service k8net-web-service --url --namespace dev`

### Enable Ingress ###
1. Addon Ingress to MiniKube
<br/>
`minikube addons enable ingress`
2. Addon Ingress DNS
<br/>
`minikube addons enable ingress-dns`
3. Check Ingress Pods
<br/>
`Kubectl get pods -n ingress-nginx`
4. Append to c://windows/system32/drivers/etc/hosts
<br/>
`127.0.0.1 dev.k8net.com`
5. Run Ingress with minikube tunnel
<br/>
`minikube tunnel`

### Create Self Signed Cert ###
1. Create Cert with bash
<br/>
`openssl req -x509 -sha256 -days 356 -nodes -newkey rsa:2048 -keyout server.key -subj "//CN=dev.k8net.com//C=SG//L=Singapore" -out server.crt`


### References ###
 - [Minikube .NET intro](https://www.hosting.work/aspnet-core-kubernetes-minikube/)
 - [Access Apps](https://minikube.sigs.k8s.io/docs/handbook/accessing/)
 - [minikube cert](https://minikube.sigs.k8s.io/docs/tutorials/custom_cert_ingress/)
 - [reference](https://stackoverflow.com/questions/58561682/minikube-with-ingress-example-not-working)
 - [Ingress,TLS,Encrypt](https://medium.com/cloud-native-journey/net-core-on-kubernetes-part-4-ingress-tls-and-lets-encrypt-3f0f6dacde36)
 - [LB and Ingress](https://medium.com/cloud-native-journey/net-core-on-kubernetes-part-3-load-balancing-and-ingress-2f565bb6a3d4)

 ### References Helm ###
 = [Kubenetes Components](https://mikehadlow.com/posts/2022-06-24-writing-dotnet-services-for-kubernetes/)
 - [Helm Example](https://andrewlock.net/deploying-asp-net-core-applications-to-kubernetes-part-4-creating-a-helm-chart-for-an-aspnetcore-app/)
 - [Helm Example2](https://github.com/saharsh-samples/dotnet-k8s-helm-cicd/blob/develop/deployment/helm-k8s/Chart.yaml)

* Other community or team contact