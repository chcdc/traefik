### Traefik K8S

#### Using Helm

```bash
helm repo add traefik https://helm.traefik.io/traefik
helm repo update
helm install traefik traefik/traefik
```
If you want to customize the Helm Chart, you can do so by changing the values in the values.ymlfile to fit your needs.

helm install traefik traefik/traefik --values values.yml


#### Using K3d

```bash
kubectl apply -f role.yml
kubectl apply -f account.yml
kubectl apply -f role-binding.yml
kubectl apply -f traefik.yml
kubectl apply -f traefik-services.yml

kubectl port-forward -n kube-system “$(kubectl get pods -n kube-system| grep '^traefik-' | awk '{print $1}')” 9000:9000
```
