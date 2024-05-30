## Comandos Principales

```
kubectl version
kubectl version --output=yaml
```

### Cliclo de Vida de un POD

- ![ciclo_de_vida](image/command/ciclo_de_vida.png)


Iniciar un POD

```
kubectl run nginx1 --image=nginx

kubectl run apache --image=httpd --port=8080

```

Obtener Informacion de pods que estan corriendo

```
kubectl get pods
kubectl get pods -o wide


kubectl describe pod/nginx
```

Comandos de ejecución

```
kubectl exec nginx -it -- bash
```

#### **Proxy:**

Permite a un servicio que esta en un POD, pueda ser accedido desde la red

```
kubectl proxy --address='0.0.0.0' --accept-hosts='^.*$'
```






