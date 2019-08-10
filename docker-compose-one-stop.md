### MySQL 

```yaml
version : '3'
services:
  mysql:
    image: mysql
    command: --default-authentication-plugin=mysql_native_password
    environment:
      MYSQL_ROOT_PASSWORD: root
    ports:
      - "3306:3306"
    volumes:
      - "./scripts/schema.sql:/docker-entrypoint-initdb.d/1.sql"
      - "./scripts/data.sql:/docker-entrypoint-initdb.d/2.sql"
```

### RabbitMQ 

```yaml
version : '3'
services:
   rabbitmq:
    image : rabbitmq:management
    ports:
      - "5672:5672"
      - "15672:15672"
```
### Solr 

```yaml
version : '3'
services:
  solr:
    image: solr:7.6
    ports:
      - "8983:8983"
    volumes:
      - ./solr_cores/IndianTowns:/opt/solr/server/solr/IndianTowns
```
