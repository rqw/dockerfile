FROM tomcat:8.5-jre8
MAINTAINER renqiwei1220@163.com
LABEL description="jenkins deploy tomcat8 manager userinfo:jenkins/jenkins"
ENV JAVA_OPTS -Xmx1024m -Xms256m -Djava.security.edg=file:/dev/./urandom
RUN  sed  -i '25a    <Resources cachingAllowed="true" cacheMaxSize="100000" />'  /usr/local/tomcat/conf/context.xml \
     && \
     sed -i '43a      <role rolename="tomcat"/>\n\
     <role rolename="jenkins"/>\n\
     <role rolename="manager"/>\n\
     <role rolename="manager-gui" />\n\
     <role rolename="manager-script" />\n\
     <role rolename="manager-status" />\n\
     <role rolename="manager-jmx" />\n\
     <user username="jenkins" password="jenkins" roles="jenkins,manager,manager-gui,manager-script,manager-status,manager-jmx"/>\n'\
 /usr/local/tomcat/conf/tomcat-users.xml \
     && \
     sed -i '19,20d' /usr/local/tomcat/webapps/manager/META-INF/context.xml \
     && \
     sed -i 's/52428800/1048576000/g' /usr/local/tomcat/webapps/manager/WEB-INF/web.xml
EXPOSE 8080
CMD ["catalina.sh", "run"]