```
helm install ms-business . --namespace=ngx-ns --set imageversion=0.1.0
helm upgrade ms-business . --namespace=ngx-ns --set imageversion=0.1.0
helm uninstall msbusiness  --namespace=ngx-ns
helm list --namespace=ngx-ns
```

### adding helm repository
```
helm repo add stable https://kubernetes-charts.storage.googleapis.com
```
[git helm/charts](https://github.com/helm/charts)



# installing helm private repository in K8s
### Ref
[How To Set Up a Private Docker Registry on Top of DigitalOcean Spaces and Use It with DigitalOcean Kubernetes](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-docker-registry-on-top-of-digitalocean-spaces-and-use-it-with-digitalocean-kubernetes)



```
ingress:
  enabled: true
  hosts:
    - <registry.example.com>
  annotations:
    kubernetes.io/ingress.class: nginx
    certmanager.k8s.io/cluster-issuer: letsencrypt-prod
    nginx.ingress.kubernetes.io/proxy-body-size: "30720m"
  tls:
    - secretName: letsencrypt-prod
      hosts:
        - <registry.example.com>

storage: s3

secrets:
  htpasswd: ""
  s3:
    accessKey: "<your_space_access_key>"
    secretKey: "<your_space_secret_key>"

s3:
  region: <your_space_region>
  regionEndpoint: <your_space_region>.digitaloceanspaces.com
  secure: true
  bucket: <your_space_name>
```


```
helm repo add stable https://kubernetes-charts.storage.googleapis.com
helm repo update
helm install docker-registry stable/docker-registry -f chart_values.yaml 
```