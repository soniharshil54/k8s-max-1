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

## Update deployment

Make a change in the code (html code) that you can identify in browser. 
rebuild the image or create a newly named image if you want. I will just be rebuilding the image here (building image with the same name but a different tag).
and then push the image to dockerhub.

```bash
docker build -t kub-first-app:2 .
docker tag a0b414f62ba3 <your-dockerhub-user-name>/kub-first-app:2
docker push <your-dockerhub-user-name>/kub-first-app
```

Here `a0b414f62ba3` in second command is the image id if the image `kub-first-app:2`.

```bash
kubectl set image deployment/first-app kub-first-app=<your-dockerhub-user-name>/kub-first-app:2
```




