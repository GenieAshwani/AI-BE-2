# Stage 1: Use Maven to build the JAR
FROM maven:3.9-eclipse-temurin-17-alpine AS builder

WORKDIR /app
COPY . .

# Build the Spring Boot app
RUN mvn clean package -DskipTests

# Stage 2: Use lightweight runtime image
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
