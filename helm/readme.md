```
helm install ms-business . --namespace=ngx-ns --set imageversion=0.1.0
helm upgrade ms-business . --namespace=ngx-ns --set imageversion=0.1.0
helm uninstall msbusiness  --namespace=ngx-ns
helm list --namespace=ngx-ns
```