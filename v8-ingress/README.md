# NGINX as ingress controller

1. check the version compatibility with your current Kubernetes version: https://github.com/kubernetes/ingress-nginx
2. Install the nginx controller (modify the controller version according to the table from the previous step):
```shell
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.3.0/deploy/static/provider/cloud/deploy.yaml
```
3. Check the public installation guide for more details (with kubectl): https://kubernetes.github.io/ingress-nginx/deploy/#quick-start
4. DEMO:

   🌵  install the demo app: ``` kubectl apply -f ./demo``` <br />
   🌵  add a new line containing ```127.0.0.1  cloud.core.com ``` to the file ```C:\Windows\System32\drivers\etc\hosts``` <br />
   🌵  access the app under ```cloud.core.com/demo``` (localhost works as well)  <br />
   🌵  to uninstall run: ```kubectl apply -f ./demo ```
5. Go to the hands-on from last time under [v9-configmaps-secrets](../v9-configmaps-secrets/)
6. Modify the two services of the ```result``` and ```vote``` apps and add two ingresses to access them on you new domain ```cloud.core.com```


kubectl create ingress demo-localhost --class=nginx --rule="demo.localdev.me/*=demo:80"
