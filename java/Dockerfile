FROM maven:3.9-eclipse-temurin-8-alpine as builder

LABEL maintainer="camillelaunois"

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

FROM eclipse-temurin:8-jre

WORKDIR /app

COPY --from=builder /app/target/java-0.0.1-SNAPSHOT.jar .

EXPOSE 8448

CMD ["java", "-jar", "java-0.0.1-SNAPSHOT.jar"]
