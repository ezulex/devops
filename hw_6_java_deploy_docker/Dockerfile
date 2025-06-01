FROM maven:3.8.6-openjdk-8-slim AS maven_build
RUN ls -la /
COPY boxfuse-sample-java-war-hello/ /app/
RUN ls -la /app/
RUN pwd
WORKDIR /app
RUN ls -la
RUN pwd
RUN mvn package

FROM tomcat:8.5.82-jdk8-openjdk-slim
COPY --from=maven_build /app/target/*.war /usr/local/tomcat/webapps/
EXPOSE 8080
CMD ["catalina.sh", "run"]