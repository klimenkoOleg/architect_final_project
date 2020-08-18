# architect_final_project

Prerequisite
1. Install Prometheus
Go to install-kuber-manual
minikube addons disable ingress
kubectl create namespace monitoring
kubectl config set-context --current --namespace=monitoring
helm install prom stable/prometheus-operator -f prometheus.yaml --atomic
helm install nginx stable/nginx-ingress -f nginx-ingress.yaml --atomic
Run Grafana:
kubectl port-forward -n monitoring service/prom-grafana 9000:80
user: admin password: prom-operator

Run Prometheus:
kubectl port-forward -n monitoring service/prom-prometheus-operator-prometheus 9090

Port froward for DB:
kubectl port-forward -n default service/myapp-postgresql 5555:5432

Установка 

1) Установка в любой namespace командой - использует helm
./install.sh 
2) Деинсталляция - командой ./uninstall.sh
3) Выполнение тестов - можно использовать экспортированную коллекцию:

newman run OtusArchIdempotancy-KlimenkoOleg.postman_collection.json


Описание

Реализован идемпотентный платеж в микросевисе PAYMENT - передается генерируемый клиентом ключ идемпотентности, в заголовке idempotanceKey, в формате UUID.
Ключ записывается в базу платежей в отдельную колонку. При каждом запросе проверяется в БД (поиск по ключу идемпотентности) - был ли уже такой для ранее принятых платежей. Если был - платеж отклоняется. 


Архиектура решения

Ouath server microservice:  https://github.com/klimenkoOleg/spring-oauth-server

API Gateway Zuul: https://github.com/klimenkoOleg/zuul-oauth2

Payment microservice: https://github.com/klimenkoOleg/otus-task9-idempotent-method



![Architecture](https://github.com/klimenkoOleg/architect_final_project/blob/master/OTUS%20Architecture%20training%20-%20Idempotancy%20lesson.png?raw=true)


To start and configure minikube:
minikube start
minikube docker-env
eval $(minikube -p minikube docker-env)



Useful commands:
To check Kafka topic content (topic named payment2)
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --from-beginning --topic payment2
