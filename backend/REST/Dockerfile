FROM maven:3.9.9-eclipse-temurin-21 AS build

WORKDIR /app

# Copy parent pom and modules
COPY pom.xml ./pom.xml
COPY DTO ./DTO
COPY REST ./REST

# Build the application
RUN mvn clean install -DskipTests

# Create runtime image
FROM eclipse-temurin:21-jre

WORKDIR /app

# Copy the built jar from build stage
COPY --from=build /app/REST/target/REST-0.0.1-SNAPSHOT.jar app.jar

# Expose the port
EXPOSE 8080

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
