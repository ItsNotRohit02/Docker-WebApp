FROM openjdk:11 AS BUILD_IMAGE

LABEL "Project"="Docker-WebApp"
LABEL "Author"="ItsNotRohit02"

RUN apt update && apt install git maven -y
RUN git clone https://github.com/ItsNotRohit02/Docker-WebApp.git
RUN cd Docker-WebApp && mvn install

FROM tomcat:9-jre11

RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE Docker-WebApp/target/Sample-v1.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]