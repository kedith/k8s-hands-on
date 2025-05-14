# V9 Configmaps & Secrets

The ```example-voting-app``` is a forked project from https://github.com/dockersamples/example-voting-app

It contains some changes which make it possible to configure the log level from an environment variable. Search for
comments of the structure ```#V9``` (in ```./vote/app.py``` and ```./k8s-specifications/vote-deployment.yaml```) to
understand the changes

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