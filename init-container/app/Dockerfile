FROM maven:3.6.3-jdk-8 as BUILD

COPY . /usr/src/app
RUN mvn -Dmaven.repo.local=/root/m2 --batch-mode -f /usr/src/app/pom.xml clean package

FROM openjdk:8-jre-slim
EXPOSE 8080
COPY --from=BUILD /usr/src/app/target /opt/target
WORKDIR /opt/target

CMD ["java", "-jar", "app.war"]

