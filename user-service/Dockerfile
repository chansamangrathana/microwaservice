FROM gradle:8.10.0-jdk17 AS builder
ENV SPRING_PROFILES_ACTIVE=dev
WORKDIR /app
COPY / .
RUN gradle build --no-daemon

FROM openjdk:17
COPY --from=builder /app/build/libs/*-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
EXPOSE 8081