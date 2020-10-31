FROM openjdk:14-alpine

RUN apk update
RUN apk --no-cache add wget unzip git maven

RUN git clone https://bitbucket.org/l2jserver/l2j-server-game.git /tmp/gameserver
RUN git clone https://bitbucket.org/l2jserver/l2j-server-datapack.git /tmp/datapack

RUN mkdir -p /usr/gameserver

WORKDIR /tmp/gameserver
RUN chmod 755 mvnw && ./mvnw install
RUN unzip target/l2j-server-game-*.zip -d /usr/gameserver

WORKDIR /tmp/datapack
RUN chmod 755 mvnw && ./mvnw install
RUN unzip target/l2j-server-datapack-*.zip -d /usr/gameserver

WORKDIR /usr/gameserver
CMD ["java", "-Xms512m", "-Xmx2g", "-jar", "l2jserver.jar"]