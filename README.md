# backend

This app should display the name of the pod and of the node.

You need to launch this application on your Kubernetes cluster in a Pod containing an environment variable called `MY_POD_NAME`.

## Run locally

```
go run main.go
2022/03/01 09:56:21 Listening on localhost:8080
```

## Docker

Run locally:

```bash
docker build -t scraly/hello-pod:1.0.0 .
docker run -it -p 8080:8080 scraly/hello-pod:1.0.0
```

Login in the private registry:

```bash
docker login [PRIVATE_REGISTRY_URL]
docker push scraly/hello-pod:1.0.0
```

## Kubernetes

```
$ kubectl apply -f deploy.yml
deployment.apps/deploy created

$ stern hello-pod
+ hello-pod-7b85865ff-wlrvz › backend
hello-pod-7b85865ff-wlrvz backend 2022/03/01 09:20:04 Listening on localhost:8080
```

## Test/Access to the app

```
curl http://localhost:8080/
```