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


