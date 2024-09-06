# Use an official Maven image as a parent image
FROM maven:3.9.9-eclipse-temurin-11 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Build the Maven project
RUN mvn clean package

# Use an official OpenJDK image as a parent image for the runtime environment
FROM openjdk:11-jre-slim

# Copy the built jar file from the build stage
COPY --from=build /app/target/spring-boot-web.jar /app/spring-boot-web.jar

# Expose the port the app runs on
EXPOSE 8080

# Run the jar file
ENTRYPOINT ["java", "-jar", "/app/spring-boot-web.jar"]
