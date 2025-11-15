*/
# You can change this base image to anything else 
# But make sure to use the correct version of Java
FROM adoptopenjdk/openjdk11:alpine-jre 
#fd
# Simply the artifact path
ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

COPY ${artifact} app.jar

# This should not be changed
ENTRYPOINT ["java","-jar","app.jar"]
*/
FROM maven:3.9.11-eclipse-temurin-11-alpine as build
WORKDIR /app
COPY pom.xml .
COPY . .
RUN mvn clean package
#Stage 2
FROM adoptopenjdk/openjdk11:alpine-jre
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
