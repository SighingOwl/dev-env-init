# 1단계: Gradle로 빌드
FROM gradle:8.13.0-jdk21-corretto AS builder
WORKDIR /app
COPY . .
RUN gradle build --no-daemon

# 2단계: 실행 컨테이너
FROM openjdk:25-ea-21-jdk-slim
WORKDIR /app
COPY --from=builder /app/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
