#stage 1: build
FROM maven:3.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn dependency:go-offline
RUN mvn package -DskipTests

#stage 2: run
FROM eclipse-temurin:25-jre-alpine AS run
WORKDIR /app
COPY --from=build /app/target/docker-lab-0.0.1-SNAPSHOT.jar .
ENTRYPOINT [ "java", "-jar", "./docker-lab-0.0.1-SNAPSHOT.jar"]

EXPOSE 8080
#CMD ["java", "-jar", "target/docker-lab-0.0.1-SNAPSHOT.jar"]
