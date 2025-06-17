kubectl apply -f k8s-web-to-nginx.yml -f nginx.yml

kubectl get deploy
kubectl get svc
kubectl get pods  

127.0.0.1:3030 -> OK!
http://127.0.0.1:3030/nginx -> OK