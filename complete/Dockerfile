FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAR_FILE
RUN apt-get update \
    && apt-get install -y --no-install-recommends openssh-server \
    && echo "root:Docker!" | chpasswd
RUN bash -c "service ssh start"
COPY sshd_config /etc/ssh/
ADD ${JAR_FILE} app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
EXPOSE 2222 80
