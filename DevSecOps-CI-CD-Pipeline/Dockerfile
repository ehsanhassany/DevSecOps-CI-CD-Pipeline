FROM maven:3.8.6-eclipse-temurin-17 AS builder
WORKDIR /build
COPY . .
RUN mvn clean package -Dlicense.skip=true

FROM tomcat:9.0-jdk17
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=builder /build/target/jpetstore.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
