FROM debian:jessie
RUN apt-get update && apt-get install -y wget
RUN cd /opt && wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u111-b14/jdk-8u111-linux-x64.tar.gz" && \
    tar xzf jdk-8u111-linux-x64.tar.gz && \
     wget http://www.eu.apache.org/dist/tomcat/tomcat-7/v7.0.75/bin/apache-tomcat-7.0.75.tar.gz && \
     tar zxpvf apache-tomcat-7.0.75.tar.gz

ENV JAVA_HOME /opt/jdk1.8.0_111
ENV CATALINA_HOME /opt/apache-tomcat-7.0.75
ENV PATH $PATH:$JAVA_HOME/bin
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/bin
ADD ./run.sh /usr/local/bin/run
EXPOSE 8080
RUN chmod +x /usr/local/bin/run
ENTRYPOINT ["/usr/local/bin/run"]
COPY hello-world-war-1.0.0.war /opt/apache-tomcat-7.0.75/webapps
RUN cd /opt/apache-tomcat-7.0.75/webapps && mv hello-world-war-1.0.0.war helloworld.war
