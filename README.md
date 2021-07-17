# k8s-max-1

## Build docker image

Build the docker image that you want to run in a kubernetes cluster.

```bash
docker build -t kub-first-app .
```

## Push your built docker image to docker hub

```bash
docker tag kub-first-app <your-dockerhub-user-name>/kub-first-app
docker push <your-dockerhub-user-name>/kub-first-app
```

## Create deployment object to run the container in a k8s cluster

```bash
kubectl create deployment first-app --image=soniharshil54/kub-first-app
```

## Expose the deployment (create service) to access the deployed container/pod from outside of cluster (host/browser).

```bash
kubectl expose deployment first-app --type=LoadBalancer --port=8080
```

## Get the ip address of the pod to access it

```bash
minikube service first-app
```

## Scale deployment to start multiple pods simultaneously for the same container

```bash
kubectl scale deployment/first-app --replicas=3
```


