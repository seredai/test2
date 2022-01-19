# 1 Кластер куба был развернут в AWS
# 2 - Установлен nginx в качестеве ингресс-контроллера
```
 https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-0.32.0/deploy/static/provider/aws/deploy.yaml
```
# 3 Установка Prometheus и Grafana в eks с помошью helm
```
kubectl create namespace prometheus
helm install prometheus prometheus-community/prometheus \
    --namespace prometheus \
    --set alertmanager.persistentVolume.storageClass="gp2" \
    --set server.persistentVolume.storageClass="gp2"
```
