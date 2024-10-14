FROM gradle:8.10.0-jdk17 AS builder
ENV SPRING_PROFILES_ACTIVE=dev
WORKDIR /app
COPY / .
# Build the application
RUN gradle build --no-daemon

FROM openjdk:17
## Copy the jar file from the build/libs directory to the Docker image
COPY --from=builder /app/build/libs/*-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
EXPOSE 8761