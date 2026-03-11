# ================================
# Stage 1: Build
# ================================
FROM gradle:jdk21 AS builder

WORKDIR /app
COPY . /app
RUN ./gradlew bootJar --no-daemon

# ================================
# Stage 2: Run
# ================================
FROM amazoncorretto:21-alpine

WORKDIR /app
COPY --from=builder /app/build/libs/my-app-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
