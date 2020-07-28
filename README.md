# architect_final_project

Установка 

1) Установка в любой namespace командой - использует helm
./install.sh 
2) Деинсталляция - командой ./uninstall.sh
3) Выполнение тестов - можно использовать экспортированную коллекцию:

newman run OtusArchIdempotancy-KlimenkoOleg.postman_collection.json


Описание

Реализован идемпотентный платеж в микросевисе PAYMENT - передается генерируемый клиентом ключ идемпотентности, в заголовке idempotanceKey, в формате UUID.
Ключ записывается в базу платежей в отдельную колонку. При каждом запросе проверяется в БД (поиск по ключу идемпотентности) - был ли уже такой для ранее принятых платежей. Если был - платеж отклоняется. 


Ouath server microservice:  https://github.com/klimenkoOleg/spring-oauth-server

API Gateway Zuul: https://github.com/klimenkoOleg/zuul-oauth2

Payment microservice: https://github.com/klimenkoOleg/otus-task9-idempotent-method



![Architecture](https://github.com/klimenkoOleg/architect_final_project/blob/master/OTUS%20Architecture%20training%20-%20Idempotancy%20lesson.png?raw=true)
