# microk8s-hetzner-deployment

 Things need to create a microk8s dev server in Hetzner

## Registry

 docker run --entrypoint htpasswd httpd:2 -Bbn youruser yourpassword > registry.password

 kubectl apply -f .\registry\registry.yaml

 kubectl create secret generic auth-secret --from-file=./registry.password -n registry

 kubectl create secret docker-registry regcred -n default --docker-server=registry.yourdomain.com --docker-username=youruser --docker-password=yourpassword --docker-email=myemail@something.com

```yaml
--
apiVersion: apps/v1
kind: Deployment
...
    spec:
      imagePullSecrets:
      - name: regcred     
      containers:      
      - name: demo
        image: registry.yourdomain.com/demo:1.2.3 
```