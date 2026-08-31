FROM maven:3.9-eclipse-temurin-21 AS builder

WORKDIR /src

COPY . .

RUN mvn clean install -DskipTests

FROM eclipse-temurin:21-jre

WORKDIR /app

COPY --from=builder /src/modules/flowable-rest/target/*.jar app.jar

ENTRYPOINT ["java","-jar","app.jar"]
