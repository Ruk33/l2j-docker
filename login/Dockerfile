FROM openjdk:14-alpine

RUN apk update
RUN apk --no-cache add wget unzip git maven

RUN git clone https://bitbucket.org/l2jserver/l2j-server-login.git /tmp/loginserver

RUN mkdir -p /usr/loginserver

WORKDIR /tmp/loginserver
RUN chmod 755 mvnw && ./mvnw install
RUN unzip target/l2j-server-login-*.zip -d /usr/loginserver

WORKDIR /usr/loginserver
COPY ./config ./config
CMD ["java", "-Xms128m", "-Xmx256m", "-jar", "l2jlogin.jar"]