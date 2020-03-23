

````
istioctl manifest apply --set profile=demo \
--set values.gateways.istio-ingressgateway.sds.enabled=true \
  --set values.global.k8sIngress.enabled=true \
  --set values.global.k8sIngress.enableHttps=true \
  --set values.global.k8sIngress.gatewayName=ingressgateway
  ````