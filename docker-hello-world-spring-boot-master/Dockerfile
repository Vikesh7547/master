# Step 1: Maven build container
FROM maven:3.8.5-openjdk-11 AS maven_build

WORKDIR /app
COPY pom.xml .
COPY src ./src

RUN mvn package -DskipTests

# Step 2: Run JAR in lightweight JDK
FROM eclipse-temurin:11-jre

EXPOSE 8086

COPY --from=maven_build /app/target/hello-world-0.1.0.jar /app/hello-world-0.1.0.jar

ENTRYPOINT ["java", "-jar", "/app/hello-world-0.1.0.jar"]
