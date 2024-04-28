FROM openjdk:11 AS BUILD_IMAGE

RUN apt-get update && \
    apt-get install -y --no-install-recommends maven && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /opt

RUN git clone https://github.com/devopshydclub/vprofile-project.git && \
    cd vprofile-project && \
    git checkout docker && \
    mvn install && \
    cd .. && \
    rm -rf vprofile-project

FROM tomcat:9.0.54-jdk11-openjdk-slim

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE /opt/vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD ["catalina.sh", "run"]
