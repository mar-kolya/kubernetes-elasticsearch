### Deploy

#### ES
```
kubectl --namespace=es create -f es-discovery-svc.yaml
kubectl --namespace=es create -f es-svc.yaml

kubectl --namespace=es create configmap elasticsearch-config --from-file=config/elasticsearch.yaml --from-file=config/log4j2.properties
kubectl --namespace=es create -f es-master.yaml

kubectl --namespace=es create -f es-data.yaml
#apparently inject is needed for kibana
kubectl --namespace=es create -f es-ingest.yaml
kubectl --namespace=es create -f es-client.yaml

kubectl --namespace=es create -f es-ingress.yaml
```

#### Kibana
```
kubectl --namespace=es create -f kibana-svc.yaml
kubectl --namespace=es create configmap kibana-config --from-file=config/kibana.yml
kubectl --namespace=es create -f kibana.yaml
kubectl --namespace=es create -f kibana-ingress.yaml
```

#### ES head:
```
kubectl --namespace=es create -f es-head-svc.yaml
kubectl --namespace=es create -f es-head.yaml
kubectl --namespace=es create -f es-head-ingress.yaml

```

https://github.com/kubernetes/contrib/tree/master/ingress/controllers/nginx/examples/tcp
provides and exmaple of how to configure TCP ports for
ingress. `tcp-configmap.yaml` is provided in this repo for this.
