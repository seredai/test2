# 1 Кластер куба был развернут в AWS
```
eksctl create cluster  --name=test-k8s
```
# 2 - Установлен nginx в качестеве ингресс-контроллера
```
 https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-0.32.0/deploy/static/provider/aws/deploy.yaml
```
# 3 Установка Prometheus и Grafana в eks с помошью helm
Prometheus 
```
kubectl create namespace prometheus
helm install prometheus prometheus-community/prometheus \
    --namespace prometheus \
    --set alertmanager.persistentVolume.storageClass="gp2" \
    --set server.persistentVolume.storageClass="gp2"
```
Grafana
```
kubectl create namespace grafana

helm install grafana grafana/grafana \
    --namespace grafana \
    --set persistence.storageClassName="gp2" \
    --set persistence.enabled=true \
    --set adminPassword='EKS!sAWSome' \
    --values ${HOME}/environment/grafana/grafana.yaml \
    --set service.type=LoadBalancer
```
# 4 Дашборд с графиком HTTP-запросов с разбивкой по коду ответа.
![image](https://user-images.githubusercontent.com/73884188/150170358-c8d9a35e-3c3d-4e90-a447-e46271d942be.png)
![image](https://user-images.githubusercontent.com/73884188/150170455-04bffb79-8392-4cf7-83e8-3e59d5c8a7e6.png)
# 5 Скриншот графика со сработавшим алертом и его определением.
![image](https://user-images.githubusercontent.com/73884188/150170600-d02911aa-a63a-4ffe-9e17-26c636da3545.png)
# Уведомления приходят в Телеграм.
![image](https://user-images.githubusercontent.com/73884188/150171621-d6570935-b9aa-41af-9e1d-cf2ab6b7cb92.png)



