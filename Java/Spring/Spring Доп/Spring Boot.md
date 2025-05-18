Spring Boot построен на основе Spring и содержит все функции Spring.

1. Нужен для автоконфигурации модулей. Для каждого модуля есть свой starter в виде зависимости,  которую нужно подключить 

2. Динамическое включение автоконфигов. Может автоматически подключать и отключать автоконфиги по условиям, например из списка зависимостей системы сборки (если есть jdbc нужен jdbc автоконфиг)

3. Dependency Management - для каждой версии бута есть список рабочих версий библиотек которые мы можем захотеть подключить. Нам не нужно указывать версии, которые мы подключаем, он следит за всем сам

**@SpringBootApplication** - главная аннотация для мейна
SpringApplication.run() возвращает контекст

В Spring в основном используются два контроллера: Controller и RestController с помощью аннотаций **@controller** и **@restcontroller** . Основное различие между @restcontroller и @controller заключается в том, что @restcontroller объединяет аннотации @controller и @ResponseBody.

**RestController:** RestController используется для создания restful веб-сервисов с помощью аннотации @RestController. Эта аннотация используется на уровне класса и позволяет классу обрабатывать запросы, сделанные клиентом. Давайте разберем аннотацию @RestController на примере. RestController позволяет обрабатывать все REST API, такие как запросы [GET](https://www.geeksforgeeks.org/how-to-make-get-method-request-in-java-spring/) , [POST](https://www.geeksforgeeks.org/how-to-make-post-request-in-java-spring/) , [Delete,](https://www.geeksforgeeks.org/how-to-make-delete-request-in-spring/) [PUT](https://www.geeksforgeeks.org/how-to-make-put-request-in-spring-boot/) .

REST означает REpresentational State Transfer (Википедия: «передача состояния представления»). Отличительной особенностью сервисов REST является то, что они позволяют наилучшим образом использовать протокол HTTP. 