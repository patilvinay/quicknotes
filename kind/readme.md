

 export PATH=$PATH:/home/vinay/go/bin

 kind get clusters
 kind delete cluster --name=registry
 kind create cluster --config=kind.yaml
 kubectl config use-context kind-kind

creating kind ingress 
 https://kind.sigs.k8s.io/docs/user/ingress/

 kubectl apply -f https://projectcontour.io/quickstart/contour.yaml
 kubectl patch daemonsets -n projectcontour envoy -p '{"spec":{"template":{"spec":{"nodeSelector":{"ingress-ready":"true"},"tolerations":[{"key":"node-role.kubernetes.io/master","operator":"Equal","effect":"NoSchedule"}]}}}}'

 kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.30.0/deploy/static/mandatory.yaml

kubectl patch deployments -n ingress-nginx nginx-ingress-controller -p '{"spec":{"template":{"spec":{"containers":[{"name":"nginx-ingress-controller","ports":[{"containerPort":80,"hostPort":80},{"containerPort":443,"hostPort":443}]}],"nodeSelector":{"ingress-ready":"true"},"tolerations":[{"key":"node-role.kubernetes.io/master","operator":"Equal","effect":"NoSchedule"}]}}}}'



install istio
```
istioctl manifest apply --set profile=demo \                                                                                                             
--set values.gateways.istio-ingressgateway.sds.enabled=true \
  --set values.global.k8sIngress.enabled=true \
  --set values.global.k8sIngress.enableHttps=true \
  --set values.global.k8sIngress.gatewayName=ingressgateway
  ```


