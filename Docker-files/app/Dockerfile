FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/Amrish24-S/test.git
RUN cd test && mvn install

FROM tomcat:9-jre11 
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE test/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]