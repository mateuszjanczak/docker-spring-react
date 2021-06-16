FROM maven:3.6-jdk-8-alpine AS builder

WORKDIR build

COPY pom.xml .

RUN mvn clean package -Dmaven.test.skip -Dmaven.main.skip -Dspring-boot.repackage.skip && rm -r target

COPY src ./src

RUN mvn clean package -Dmaven.test.skip

COPY target/*.jar server.jar

RUN java -Djarmode=layertools -jar server.jar extract

FROM openjdk:8-jre-alpine

WORKDIR server

COPY --from=builder build/dependencies .
COPY --from=builder build/spring-boot-loader .
COPY --from=builder build/snapshot-dependencies .
COPY --from=builder build/application .

EXPOSE 8080

ENTRYPOINT ["java", "org.springframework.boot.loader.JarLauncher"]
