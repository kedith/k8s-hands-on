# Service Configuration with YAML

## 1. Hands-on: internal access (inside the cluster)
Launch the student app(REST API, 5000 Port) in Pod(Single Instance) and expose the PORT to the **internal cluster**.

1. Create a yaml file for the pod (public [docs](https://kubernetes.io/docs/concepts/workloads/pods/) for inspiration):
    - Image: sureshkvl/test:1-2
    - labels - app:hello
    - containerPort: 5000
   
2. create a pod using this yaml file (```kubectl apply -f```)
3. Create a service yaml file:
   - selector: "app:hello“
   - port: 5000
4. Create a service using this yaml file (as in 2.)
5. Deploy the busybox pod (from the given repo above)
6. Access the app from another pod:
   - Use busybox containers to debug the service
     - https://kubernetes.io/docs/tasks/debug/debug-application/debug-service/ 
   - Use the curl container to access the app and run: curl http://hello1/students
7. Delete the resources created  (pod, service) 

## 2. Hands-on: external access (from outside the cluster, ex. browser)

Launch the student app(REST API, 5000 Port) in Pod(Single Instance) and expose the PORT to the **outside**.

Same as before but with a **different service type** (NodePort) and access the app from your browser using
the node IP and the port assigned by Kubernetes.

![img.png](./img/nodeport.png)


## 3. Hands-on: external access (from outside the cluster, ex. browser)

Launch the student app(REST API, 5000 Port) with **loadbalancing** and **high availability**, and expose the PORT to **outside**

Now you need to create a deployment with 3 replicas and a service of type NodePort. The service will load balance
the traffic between the 3 replicas and expose the app to the outside. Access the app from your browser using the node IP
and the port assigned by Kubernetes. 

Scale the app down to 2 replicas (use kubectl). Check it out (kubectl get pods)


