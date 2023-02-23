**Installation on Kompose**

```
curl -L https://github.com/kubernetes/kompose/releases/download/v1.28.0/kompose-linux-amd64 -o kompose
chmod +x kompose
sudo mv ./kompose /usr/local/bin/kompose
```

To convert <code>docker-compose.yml</code> to kubernetes

```
kompose convert
```

It will generates related YAML file for kubernetes deployment

Create the deployment

```
kubectl create -f grafana-deployment.yaml \
               -f grafana-service.yaml \
               -f influx-deployment.yaml \
               -f influx-service.yaml \
               -f telegraf-deployment.yaml

kubectl expose deployment grafana --type=NodePort --name=grafexp
```

To activate the service

```
kubectl service grafexp --url
```