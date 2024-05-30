## Comandos Principales

```
kubectl version
```
```
kubectl version --output=yaml
```

### Cliclo de Vida de un POD

![ciclo_de_vida](image/command/ciclo_de_vida.png)


#### Caracteristicas de una APP desplegada en un POD 
- una imagen se desplegara como contenedor dentro de un pod
- el POD asignara direccion , puertos, hostname, sockets, memoria
- el pod estara asosisdo a un cluster 
- otra caracteristica es que un pod se puede replicar
- los pod no tienen estado, NO se debe guardar informacion en ellos


![appPod](image/command/appPod.png)


#### Iniciar un POD

- Metodo imperativo ( comandos)
- Metodo Declarativo ( manifest yaml)

```
kubectl run nginx1 --image=nginx
```
```
kubectl run apache --image=httpd --port=8080
```

#### Obtener Informacion de pods que estan corriendo
- con la opcion ``` -o wide ```  obtenemos mas informacion 

```
kubectl get pods
```
```
kubectl get pods -o wide
```

- La opcion ``` describe ```  debe ser usada indicando el tipo de recurso ```pod/...```
- Se obtiene informacion como:
    - name
    - namespace ( default )
    - Volumes
    - IP 
```
kubectl describe pod/nginx
```

#### Comandos de ejecución sobre los PODS

- ejecutar el comando ``` ls ``` en contenedor nginx que tenemos corriendo
```
kubectl exec nginx -- ls
```

- ingresar al contenedor nginx en modo interactivo con la shell ( exit para salir)
```
kubectl exec nginx -it -- bash
```

- ejecutar  ``` -- uname -a ``` , para obtenere caracteristicas del contenedor  
```
kubectl exec nginx -- uname -a
```

```
kubectl run apache --image=httpd --port=8080
```

#### Obtener el log de un POD ( ejemplo pod ```apache```)
```
kubectl logs apache
```
- se mantiene en escucha del log
```
kubectl logs -f apache
```

- Usar TAIL para ver las ultimas lineas

```
kubectl logs apache --tail=30
```





#### **Proxy:**
- habilita un puerto por el cual se puede reguntar por las caracteristicas y estado de las Apps localhost:8001

```
kubectl proxy --address='0.0.0.0' --accept-hosts='^.*$'
```
- api general
    - http://localhost:8001/version

- Version
    - http://localhost:8001/version

- Healthz
    - http://localhost:8001/healthz
    return ok 

#### Acceder al pod a través de la API
- http://localhost:8001/api/v1/namespaces/default/pods/nginx2 
- se observa un json con toda la informacion del pod consultado

- http://10.31.193.170:8001/api/v1/namespaces/default/pods/nginx2/proxy/

- Se accede al servicio desplegado 


![home_nginx](image/command/home_nginx.png)


#### probar el pod con un Servicio 
- 






