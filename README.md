# Knote - Kubernetes aplicacion de notas

Fork de [jilopezv-udem/knote](https://github.com/jilopezv-udem/knote)

Aplicación de notas con soporte de imágenes usando Minio como 
almacenamiento externo (stateless), desplegada en Kubernetes.

## Cambios realizados

- Integración con Minio para almacenamiento de imágenes
- Eliminación de dependencia del sistema de archivos local del pod
- Nuevos archivos de configuración de Kubernetes para Minio

## Requisitos previos

- Docker Desktop instalado y corriendo
- Minikube instalado
- kubectl instalado

## Cómo ejecutar

### 1. Iniciar Minikube

```bash
minikube start --driver=docker
```

### 2. Clonar el repositorio

```bash
git clone https://github.com/sebastian-rendon/knote-sebastian.git
cd knote-sebastian
```

### 3. Desplegar en Kubernetes

```bash
kubectl apply -f kube
```

### 4. Verificar que los pods estén corriendo

```bash
kubectl get pods
```

Esperar a que los tres pods estén en estado `Running`:
- knote
- mongo  
- minio

### 5. Abrir la aplicación

```bash
minikube service knote --url
```

Abrir la URL que aparece en el navegador.

## Imágenes en DockerHub

- `sebastianrendon/knote:2.0.0` — aplicación Knote con soporte Minio
- `sebastianrendon/minio:latest` — imagen de Minio
