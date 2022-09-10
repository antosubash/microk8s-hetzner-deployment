# microk8s-hetzner-deployment

 Things need to create a microk8s dev server in Hetzner

## Registry

 docker run --entrypoint htpasswd httpd:2 -Bbn youruser yourpassword > registry.password

 kubectl apply -f .\registry\registry.yaml

 kubectl create secret generic auth-secret --from-file=./registry.password -n registry
