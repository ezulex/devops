FROM maven:3.8.7-openjdk-18-slim AS maven_build
WORKDIR /app
COPY boxfuse-sample-java-war-hello/ ./
RUN mvn package

FROM tomcat:jdk21-openjdk-slim
COPY --from=maven_build /app/target/*.war /usr/local/tomcat/webapps/
EXPOSE 8080
CMD ["catalina.sh", "run"]