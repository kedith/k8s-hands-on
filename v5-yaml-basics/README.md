# V5 YAML basics, Deployments, Services

**GOAL:** Launch the student app(REST API, 5000 Port) in Pod(Single Instance) and expose the PORT to the **internal cluster**.

All the resources referenced in the next steps are in the ```k8s-resources``` folder

## Steps

1. Create a yaml file for the pod (public [docs](https://kubernetes.io/docs/concepts/workloads/pods/) for inspiration):
   - Image: httpd:latest
   - labels - app:hello
   - containerPort: 5000
2. create a pod using this yaml file (```kubectl apply -f <FILE_NAME>```)
3. Create a service yaml file:
   - selector: "app:hello“
   - port: 5000
4. Create a service using this yaml file (as in 2.)
5. Deploy the busybox pod (from the given repo above)
6. Access the app from another pod:
   - Use busybox containers to debug the service
     - https://kubernetes.io/docs/tasks/debug/debug-application/debug-service/
   - Use the curl container to access the app and run: ```curl http://hello1/students```
7. Delete the resources created  (pod, service) 