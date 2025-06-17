- node v24.2.0
- npm



### Императивный подход 

kubectl create deploy k8s-web-hello --image=clark666/k8s-web-hello

kubectl get pods ->
k8s-web-hello-595697c447-2js8n   1/1     Running   0          15m

(new tab:  minikube tunnel)

kubectl expose deploy k8s-web-hello --type=LoadBalancer --port=3333 --target-port=3000

kubectl get svc -> 
k8s-web-hello     LoadBalancer   10.96.204.104    127.0.0.1     3333:31961/TCP   117s


http://localhost:3333/ -> 
VERSION 1: Hello from the k8s-web-hello-595697c447-2js8n



kubectl scale deploy k8s-web-hello --replicas=3

kubectl get pods ->
k8s-web-hello-595697c447-2js8n   1/1     Running   0          17m
k8s-web-hello-595697c447-2kw7r   1/1     Running   0          25s
k8s-web-hello-595697c447-6sl28   1/1     Running   0          25s


### Декларативный подход 

kubectl apply -f deployment.yml 

kubectl get pods -o wide -> 
k8s-web-hello-6bdd6996ff-xwdk6   1/1     Running   0          3m58s   10.244.0.13   minikube   <none>           <none>

curl 10.244.0.13:3000 -> OK!

kubectl apply -f service.yml   
-> 10.103.65.62     127.0.0.1     3030:31061/TCP  

 127.0.0.1:3030 -> OK!