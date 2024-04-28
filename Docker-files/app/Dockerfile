FROM openjdk:11 AS BUILD_IMAGE

RUN apt-get update && apt-get install -y maven \
    && apt-get clean

RUN git clone --branch docker https://github.com/avin187/vprofile-project.git  && \
    cd vprofile-project && \
    mvn install

FROM tomcat:9-jre11

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD ["catalina.sh", "run"]