# Stage 1 — Build JAR
FROM maven:3.9.9-amazoncorretto-11 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

# Stage 2 — Run JAR
FROM amazoncorretto:11-alpine-jdk

WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8084

CMD ["java","-jar","app.jar"]
