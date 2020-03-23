

installing kubernetes dashboard

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc6/aio/deploy/recommended.yaml


create service account
kubectl apply -f serviceAccount.yaml 

creating rolebinding
kubectl apply -f RoleBinding.yaml 


get secret
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}') 


kubectl proxy


kubectl create ns ngx-ns

kubectl label namespace ngx-ns istio-injection=enabled

helm install ms-business  . --namespace=ngx-ns --set imageversion=0.1.0