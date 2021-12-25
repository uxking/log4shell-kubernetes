# Log4shell Vulnerable app deployment on kubernetes
Use this to view how a log4shell exploitable app responds to various queries and headers

**Notes:**
- Using traefik as the IngressController
- `log4shell-vuln-app.yml` will deploy a vuln app to your k8s cluster with 1 replica
- Ingress configured to listen on port 80 at the specified hostname

If you need to install Traefik, you can take a look at the sameple `values.yml` file and deploy using helm with:  
 `helm install traefik traefik/traefik --values=values.yml`

 Thanks to [Github user xcad2k](https://github.com/xcad2k/boilerplates/tree/main/kubernetes/traefik) for `values.yml` boilerplate.

 Once Traefik is running use the `kubectl get all` (in the namespace where Traefic is installed) to view the **EXTERNAL-IP** for your cluster.  
 Look for:  
 ```
NAME                     TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)                      AGE
service/traefik          LoadBalancer   10.43.84.87    172.27.88.134   80:30818/TCP,443:32612/TCP   32h
```
Use the external IP for DNS or host file to allow you to resolve a host url.
