#FROM gradle:4.7.0-jdk8-alpine AS build
#COPY --chown=gradle:gradle . /home/gradle/src
#WORKDIR /home/gradle/src
#RUN gradle build --no-daemon

FROM openjdk:8-jre-slim

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y locales

RUN sed -i -e 's/# es_ES.UTF-8 UTF-8/es_ES.UTF-8 UTF-8/' /etc/locale.gen && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=es_ES.UTF-8

ENV LANG es_ES.UTF-8
ENV LANGUAGE es_ES:es
ENV LC_ALL es_ES.UTF-8

EXPOSE 8443

#COPY SSL0132907.pem SSL0132907.pem
#COPY SSLpreving.cer SSLpreving.cer

#RUN openssl x509 -in SSL0132907.pem -inform pem -out SSL0132907.der -outform der

#RUN echo yes | keytool -importcert -alias startssl -keystore \
#    $JAVA_HOME/lib/security/cacerts -storepass changeit -file SSLpreving.cer


RUN mkdir /app && \
    mkdir /app/recursos && \
	mkdir /app/recursos/trabajadores && \
    mkdir /app/templates

COPY ./build/libs/*.jar /app/spring-boot-application.jar

COPY ./src/main/resources/reports/templates/auditoria-finalizada.odt /app/templates/auditoria-finalizada.odt

ENTRYPOINT ["java", "-XX:+UnlockExperimentalVMOptions", "-XX:+UseCGroupMemoryLimitForHeap", "-Djava.security.egd=file:/dev/./urandom","-jar", "-Duser.country=ES", "-Duser.language=es","/app/spring-boot-application.jar"]
