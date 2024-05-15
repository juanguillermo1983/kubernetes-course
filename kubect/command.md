Comandos Principales

```
kubectl version
kubectl version --output=yaml
```

Proxy para hacer proxy de un servicio que esta en un POD, pueda ser accedido desde la red

```
kubectl proxy --address='0.0.0.0' --accept-hosts='^.*$'
```
