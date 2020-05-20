Каталог 'crud-chart' содержит Helm-сборку приложения.

Файл 'postgres-exporter-values.yaml' необходим для запуска Postgres-экспортера для Prometheus (https://github.com/helm/charts/blob/master/stable/prometheus-postgres-exporter). Вместо '...' в файле требуется указать IP-адрес миникуба (можно определить, например, с помощью команды minikube ip) и порт, на который произошел mapping базы Postgres приложения. Команда для запуска экспортера: 'helm install -f postgres-exporter-values.yaml myapp-postgres-exporter stable/prometheus-postgres-exporter' (вместо 'myapp-postgres-exporter', конечно, можно указать любое другое имя).

Создается 4 дашборда:
1. "CRUD" - Latency, RPS и Error Rate(количество полученных ошибок 500) для приложения.
2. "CRUD(Nginx controller)" - Latency, RPS и Error Rate(количество полученных ошибок 500) для Nginx-контроллера.
3. "CRUD(resources usage)" - использование CPU и памяти подами приложения.
4. "CRUD(Postgres)" - метрики Postgres, поставляемые экспортером (размер БД, количество locks и deadlocks, возникающих в БД, а также некоторые выборки из 'pg_stat_statements' (сколько раз выполнен тот или иной запрос, среднее и максимальное время выполнения запроса)).
*для возникновения ошибок 500 была удалена пода с Postgres (с ее дальнейшим автоматическим перезапуском)

Каталог 'grafana-screenshots' содержит некоторые скриншоты дашбордов.
