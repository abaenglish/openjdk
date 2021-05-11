FROM adoptopenjdk/openjdk11-openj9@sha256:112fb3c07e9ede2f46cc6bc7ac54803422cb58a776dc87c684ef403ead058134

ENV JAVA_TOOL_OPTIONS="$JAVA_TOOL_OPTIONS $JAVA_AGENT $JAVA_OPTS"

RUN addgroup -S java && adduser -S -G java java

USER java:java
