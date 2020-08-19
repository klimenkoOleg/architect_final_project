# architect_final_project


Установка 

1) Установка в любой namespace командой - использует helm
./install.sh 
2) Деинсталляция - командой ./uninstall.sh
3) Выполнение тестов - можно использовать экспортированную коллекцию:

newman run OtusArchIdempotancy-KlimenkoOleg.postman_collection.json


Описание
Находтся в saga-lesson/SAGA.pdf

Тесты 
Находят в saga-lesson/OtusArch-KlimenkoOleg.postman_collection.json (запускать сверху вниз - последовательно)



Комопненты
Ouath server microservice:  https://github.com/klimenkoOleg/spring-oauth-server

API Gateway Zuul: https://github.com/klimenkoOleg/zuul-oauth2

Payment microservice: https://github.com/klimenkoOleg/otus-task9-idempotent-method

Processing: https://github.com/klimenkoOleg/otus-task9-idempotent-method.git

Payment System: https://github.com/klimenkoOleg/otus-payment-system.git






