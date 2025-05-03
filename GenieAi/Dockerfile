# Stage 1: Build the app using Maven
FROM maven:3.6.3-openjdk-8 AS build

WORKDIR /app
COPY pom.xml .           # Make sure this file is in your Git repo root
RUN mvn dependency:go-offline

COPY . .                      # Copy source files
RUN mvn clean package -DskipTests

# Stage 2: Use a smaller image to run
FROM openjdk:8-jdk-slim

WORKDIR /app
COPY --from=build /app/target/GenieAi-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
