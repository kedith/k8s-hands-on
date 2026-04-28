# NGINX as ingress controller

1. check the version compatibility with your current Kubernetes version: https://github.com/kubernetes/ingress-nginx
2. Install the nginx controller (modify the controller version according to the table from the previous step):
```shell
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.3.0/deploy/static/provider/cloud/deploy.yaml
```
3. Check the public installation guide for more details (with kubectl): https://kubernetes.github.io/ingress-nginx/deploy/#quick-start
4. **DEMO**:

   🌵  install the demo app: ``` kubectl apply -f ./demo``` <br />
   🌵  add a new line containing ```127.0.0.1  cloud.xperience.com ``` to the file ```C:\Windows\System32\drivers\etc\hosts``` <br />
   🌵  access the app under ```cloud.xperience.com/demo``` (localhost works as well)  <br />
   🌵  to uninstall run: ```kubectl delete -f ./demo ```

5. Go to the hands-on project called ```example-voting-app``` and make sure the app is running (follow the instructions from the README file in that folder)
6. Modify the two services of the ```result``` and ```vote``` apps and add two ingresses to access them on your new domain ```cloud.xperience.com```