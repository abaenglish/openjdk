# Supported tags and respective `Dockerfile` links

- [`8-jre` (*8-jre/Dockerfile*)](8-jre/Dockerfile)
- [`8-jre-zulu` (*8-jre-zulu/Dockerfile*)](8-jre/Dockerfile)
- [`11-jre-openj9` (*11-jre-openj9/Dockerfile*)](11-jre-openj9/Dockerfile)
- [`11-alpine-jre-openj9` (*11-alpine-jre-openj9/Dockerfile*)](11-alpine-jre-openj9/Dockerfile)
-
# What is this image?

Base image to execute JVM applications focused on Spring Boot applications.
8-jre is based on [openjdk:8-jre-alpine](https://hub.docker.com/_/openjdk/)
8-jre-zulu is based on [azul/zulu-openjdk-alpine:8u252-jre](https://hub.docker.com/r/azul/zulu-openjdk-alpine)
11-jre-openj9 is based on [adoptopenjdk/openjdk11-openj9:alpine-jre](https://hub.docker.com/r/adoptopenjdk/openjdk11-openj9/)
11-alpine-jre-openj9 is based on [adoptopenjdk/openjdk11-openj9:alpine-jre](https://hub.docker.com/r/adoptopenjdk/openjdk11-openj9/) with a fixed base image to avoid latest tag pitfalls. Used for jib builds to avoid fat jars and entrypoint.sh

# How to use this image

This image adds an entrypoint.sh that allows the execution of java applications as user java:java and PID 1.

Example of a Dockerfile using this base image:
```
FROM image:tag

COPY yourapp.jar .

ENTRYPOINT ["./entrypoint.sh", "yourapp.jar"]
```

## Environment Variables

The following environment variables can be set to tune java execution.

### `JAVA_AGENT`
e.g., --java_agent:/etc/agent/newrelic.jar (loaded as a volume)

### `JAVA_OPTS`
e.g., --Xmx32m -Xss256k

## Extensions for Java 8

- [Java Cryptography Extension](https://en.wikipedia.org/wiki/Java_Cryptography_Extension)
