
# Proyecto-SD-Kubernetes101
## Juliana Zúñiga
## Código: A00068120

### Objetivo:
Construir y desplegar una app sencilla de Python en Kubernetes.

### Acerca de Kubernetes

Kubernetes coordina un cluster de computadores de alta disponibilidad que se conecta como una única unidad para trabajar. Las abstracciones en Kubernetes permite desplegar aplicaciones contenidas en un cluster sin necesidad de atarlas a una máquina individual.

Kubernetes automatiza la distribución y la programación de los contenedores de las aplicaciones a lo largo del cluster de forma eficiente. Un cluster Kubernetes está compuesto por dos tipos de recursos, los cuales son mostrados en la Figura 1:

<img src="https://d33wubrfki0l68.cloudfront.net/99d9808dcbf2880a996ed50d308a186b5900cec9/40b94/docs/tutorials/kubernetes-basics/public/images/module_01_cluster.svg">
Figura 1: Cluster Kubernetes


### Preparación del ambiente de Kubernetes mediante la instalación de minikube.

Instalar VirtualBox

Instalar Docker Toolbox for Windows

Instalar la última versión de Minikube for Windows

### Configuración

Para verificar el estado de minikube:

```
minikube status
```

Consultar versión de minikube:

```
minikube version
```

Lanzar minikube

```
minikube start
```

<img src="http://ricardodelgado.com.co/sd/7.PNG">

Se puede comprobar en VirtualBox la VM corriendo

<img src="http://ricardodelgado.com.co/sd/8.PNG">

### Despliegue del proyecto.

Construir una imagen de docker desde un proyecto existente en python

```
cd Docker
```

<img src="http://ricardodelgado.com.co/sd/1.PNG">

```
docker build -t rocco522/web .
docker push rocco522/web
```

<img src="http://ricardodelgado.com.co/sd/4.PNG">

<img src="http://ricardodelgado.com.co/sd/4.5.PNG">

Lanzar la aplicación con Docker compose
```
docker-compose up -d
```

<img src="http://ricardodelgado.com.co/sd/5.5.PNG">

Probar la aplicación
```
curl localhost:5000
```
<img src="http://ricardodelgado.com.co/sd/6.PNG">

### Inicio del servicio en kubernetes

Desplegar la aplicación en Kubernetes
```
cd ../Kubernetes
kubectl create -f db-pod.yml
kubectl create -f db-svc.yml
kubectl create -f web-pod.yml
kubectl create -f web-svc.yml
kubectl create -f web-rc.yml
```

Verificar que los pods y los servicios fueron creados
```
kubectl get pods
kubectl get svc
```

Obtener el NodePort para el servicio web.
```
kubectl describe svc web
```

Probar la app
```
kubectl get nodes
curl IP:PUERTO
```
