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

### Dockerfile for Tomcat

```
FROM tomcat:latest
ADD sample.war /usr/local/tomcat/webapps/
EXPOSE 8080
CMD ["catalina.sh", "run"]
```

#### Commands to build & run image from above Dockerfile
> docker build -t sample .

* Don't miss the . (dot) in above command

> docker run -p 8080:8080 sample


#### Docker command to check logs

First list the docker containers running currently 

> docker ps

Now copy container id from the above command's result

> docker logs <container-id copied from above command>

#### Docker command to check tomcat logs 

start bash inside Docker container

> docker exec -it <container-id> bash
  
In bash, navigate to tomcat logs folder 

> cd /usr/local/tomcat/logs/
  
Now tail the log files to get application log

> tail -f <log-file-name.log>
