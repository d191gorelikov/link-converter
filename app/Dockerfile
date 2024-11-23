FROM maven:3.9.3-eclipse-temurin-20-alpine as builder
ARG VERSION=${VERSION}
WORKDIR /usr/src/app
COPY ./src ./src
COPY *.xml ./
RUN mvn package -Dversion.application=${VERSION} -Dmaven.test.skip=true

FROM openjdk:16

#Create app directory
WORKDIR /usr/src/app
ARG VERSION=${VERSION}
RUN curl https://storage.yandexcloud.net/cloud-certs/CA.pem -o YandexInternalRootCA.crt && \
    keytool -importcert -file YandexInternalRootCA.crt -alias yandex -cacerts -storepass changeit -noprompt && \
    rm -f YandexInternalRootCA.crt
COPY --from=builder /usr/src/app/target/trouble-${VERSION}.jar ./trouble.jar


ENTRYPOINT ["java", "-jar", "./trouble.jar"]
EXPOSE 8080

