
- download

```
for f in custom-metrics-apiserver-auth-delegator-cluster-role-binding.yaml custom-metrics-apiserver-auth-reader-role-binding.yaml custom-metrics-apiserver-deployment.yaml custom-metrics-apiserver-resource-reader-cluster-role-binding.yaml custom-metrics-apiserver-service-account.yaml custom-metrics-apiserver-service.yaml custom-metrics-apiservice.yaml custom-metrics-cluster-role.yaml custom-metrics-config-map.yaml custom-metrics-resource-reader-cluster-role.yaml hpa-custom-metrics-cluster-role-binding.yaml; do curl -o $f https://github.com/kubernetes-sigs/prometheus-adapter/raw/master/deploy/manifests/$f; done
```

- replace images

```
sed 's#        image: gcr.io/k8s-staging-prometheus-adapter-amd64#        image: directxman12/k8s-prometheus-adapter-amd64#g' -i ./custom-metrics-apiserver-deployment.yaml
sed 's#  namespace: custom-metrics#  namespace: prom#g' -i *.yaml
sed 's#apiVersion: apiregistration.k8s.io/v1beta1#apiVersion: apiregistration.k8s.io/v1#g' -i *.yaml
```
