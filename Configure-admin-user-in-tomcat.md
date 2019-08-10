# Configure Admin User in Tomcat

#### In {TOMCAT_DIRECTORY}/conf/tomcat-users.xml file, add the following lines

```xml
 <role rolename="manager-gui"/>
 <role rolename="manager-script"/>
 <user username="admin" password="admin" roles="manager-gui,manager-script"/>
```
