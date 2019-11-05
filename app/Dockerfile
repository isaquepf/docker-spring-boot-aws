FROM maven:3-jdk-11-slim AS MAVEN_BUILD

COPY pom.xml /build/

COPY src /build/src/

WORKDIR /build/

RUN mvn package

FROM openjdk:11-jre-alpine

WORKDIR /app

COPY --from=MAVEN_BUILD /build/target/docker-to-aws-with-java-0.0.1-SNAPSHOT.jar /app/

ENTRYPOINT ["java", "-jar", "docker-to-aws-with-java-0.0.1-SNAPSHOT.jar"]
