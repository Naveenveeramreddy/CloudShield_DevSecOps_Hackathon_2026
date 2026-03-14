# ---------- Stage 1: Build the application ----------
FROM maven:3.9.9-eclipse-temurin-17 AS build

WORKDIR /app

# Copy entire project
COPY . .

# Build the Spring Boot JAR
RUN mvn clean package -DskipTests


# ---------- Stage 2: Run the application ----------
FROM eclipse-temurin:17-jdk-jammy

WORKDIR /app

# Copy built JAR from build stage
COPY --from=build /app/target/*.jar app.jar

# Expose Spring Boot port
EXPOSE 8080

# Run Spring Boot
ENTRYPOINT ["java","-jar","app.jar"]
