FROM maven:3.9.11-eclipse-temurin-11-alpine as build
WORKDIR /app
COPY pom.xml .
COPY . .
RUN mvn clean package
#Stage 2
FROM adoptopenjdk/openjdk11:alpine-jre
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8001
ENTRYPOINT ["java","-jar","app.jar"]
