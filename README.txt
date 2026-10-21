# K3s + Traefik + PostgreSQL

These example files were created for Zehnmind.

K3s is started on Windows with k3d. Traefik is the default ingress in K3s.

Usage:

1. Create cluster:
```
   k3d cluster create demo -p "8080:80@loadbalancer" -p "5432:5432@loadbalancer"
```
2. Build the image from the app folder:
```
   docker build -t my-web:1.0 ./app
```
3. Upload the image to the cluster:
```
   k3d image import my-web:1.0 -c demo
```
4. Apply manifests from the k8s folder:
```
   kubectl apply -f k8s/
```

Web page: http://localhost:8080

PostgreSQL (DBeaver): localhost:5432, database: appdb, user: appuser, password: apppass123.

Database files are stored in a persistent volume, so data stays after the pod is deleted (`kubectl delete pod postgres-0`).