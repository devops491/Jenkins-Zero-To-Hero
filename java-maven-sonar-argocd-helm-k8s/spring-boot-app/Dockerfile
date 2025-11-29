# Build stage
FROM maven:3.9.4-eclipse-temurin-11 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests


# Runtime stage
FROM eclipse-temurin:11-jre-alpine
WORKDIR /opt/app
COPY --from=build /app/target/spring-boot-web.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
