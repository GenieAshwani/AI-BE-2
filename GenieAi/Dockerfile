# Stage 1: Build the Spring Boot app using Maven
FROM eclipse-temurin:17-jdk-alpine AS builder

WORKDIR /app
COPY . .

# Use Maven wrapper if present
RUN ./mvnw clean package -DskipTests

# Stage 2: Run the built app
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
