# Example voting app

The ```example-voting-app``` is a forked project from https://github.com/dockersamples/example-voting-app

[Here](./README-forked.md) is the initial readme of the forked project.

## Run the app in Kubernetes

To run the app you need to:

1. build the vote app (inside the ```vote``` folder):

```shell
docker build -t examplevotingapp_vote:local .
```

2. deploy the kubernetes resources (inside the ```example-voting-app``` folder):

```shell 
kubectl apply -f k8s-specifications
```

3. The `vote` web app is then available on port 31000 on each host of the cluster, the `result` web app is available on
   port 31001.
4. To remove them, run:

```shell
kubectl delete -f k8s-specifications/
```