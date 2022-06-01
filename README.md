# Helm Task

## Steps

### In pythonApp folder: open terminal:
- Bulid image from python app by using Dockerfile
```sh
docker build -f Dockerfile -t moutazmuhammad/pythonapp .
```
- Push image to DockerHub
```sh
docker push moutazmuhammad/pythonapp
```

### Helm:
- Create Helm Chart
```sh
helm create helmTask
```
- Check on identation 
```sh
helm lint ./helmTask
```
- Show all yaml files and its values 
```sh
helm template ./helmTask
```
- Apply helm and define release name 
```sh
helm install pythonapp ./helmTask
```
- Check all deployments and services using kubectl 
```sh
kubectl get all
```
![Build Status](https://github.com/moutazmuhammad/AWS-Terraform-Task/blob/main/img/5.png?raw=true)

- User This command to get [ IP:port ] to access Python App 
> Note: IF you use minikube
```sh
minikube service frontend-svc  --url
```

### Installing kube-prometheous-stack:
- Add helm repo
```sh
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
- Install Prometheus
```sh
helm install prometheus  prometheus-community/kube-prometheus-stack
```
- Show Services:
```sh
kubectl get svc
```
- To Monitor node:
```sh
kubectl port-forward svc/prometheus-prometheus-node-exporter 9100
```
In your browser: 127.0.0.1:9100
![Build Status](https://github.com/moutazmuhammad/AWS-Terraform-Task/blob/main/img/5.png?raw=true)
- To Monitor Prometheus itself:
```sh
kubectl port-forward svc/prometheus-operated 9090
```
In your browser: 127.0.0.1:9090
![Build Status](https://github.com/moutazmuhammad/AWS-Terraform-Task/blob/main/img/5.png?raw=true)
- Grafana
```sh
kubectl port-forward deployment/prometheus-grafana 3000
```
In your browser: 127.0.0.1:3000
> Note: grafana-username: admin , grafana-password: prom-operator
![Build Status](https://github.com/moutazmuhammad/AWS-Terraform-Task/blob/main/img/5.png?raw=true)


