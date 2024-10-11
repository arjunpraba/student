# Use an official Maven image with OpenJDK 17
FROM maven:3.9.9-eclipse-temurin-17 AS build

# Set the working directory
WORKDIR /app

# Copy the pom.xml and source code
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests

# Use a lightweight image for the final app
FROM eclipse-temurin:17-jdk AS runtime

# Set the working directory
WORKDIR /app

# Copy the jar file from the build stage
COPY --from=build /app/target/your-application-name.jar app.jar

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
