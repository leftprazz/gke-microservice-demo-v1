FROM openjdk:7-jdk-alpine

RUN apk add --no-cache maven

WORKDIR /code

ADD pom.xml /code/pom.xml
RUN ["mvn", "dependency:resolve"]
RUN ["mvn", "verify"]

# Adding source, compile, and package into a fat jar
ADD src /code/src
RUN ["mvn", "package"]

CMD ["java", "-jar", "target/worker-jar-with-dependencies.jar"]
