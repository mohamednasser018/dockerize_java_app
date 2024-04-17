FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
Run git clone https://github.com/devopshydclub/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jrell
LABEL "project"="Vprofile"
LABEL "Author"="imran"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-w2.war  /usr/local/tomcat/webapps/ROOt.war 
EXPOSE 8080
CMD ["catalina.sh", "run"]