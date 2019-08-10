# Deploying Spring Boot Application in Standalone Tomcat
To deploy applications developed in Spring boot in standalone tomcat, following changes needs to be done

#### In Main Class
```java
public class SimpleRestApp extends SpringBootServletInitializer {

    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
         return application.sources(SimpleRestApp.class);
    }

    public static void main(String[] args) {
         SpringApplication.run(SimpleRestApp.class, args);
    }
}
```
#### In pom.xml
```xml
<packaging>war</packaging>

<build>
  <finalName>SimpleRestApp</finalName>
    ....
</build>
```
