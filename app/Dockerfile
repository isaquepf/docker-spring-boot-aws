FROM maven:3.6.1-jdk-11-slim AS MAVEN_BUILD
WORKDIR /build
COPY /pom.xml /build/
COPY /src /build/src/

WORKDIR /build/
RUN mvn clean package

FROM openjdk:11-jre-slim
VOLUME /tmp

COPY --from=MAVEN_BUILD /build/target/ app
RUN "ls"
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","app/docker-to-aws-with-java-0.0.1-SNAPSHOT.jar"]
