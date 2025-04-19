# Stage 1: Build the WAR file
FROM maven:3.8.6-eclipse-temurin-17 AS builder
WORKDIR /build
COPY . .
RUN mvn clean package

# Stage 2: Create the Tomcat image
FROM tomcat:9.0-jdk21-temurin
# Clean default webapps
RUN rm -rf /usr/local/tomcat/webapps/*
# Copy WAR from builder stage
COPY --from=builder /build/target/*.war /usr/local/tomcat/webapps/ROOT.war
# Expose default Tomcat port
EXPOSE 8080
# Run Tomcat
CMD ["catalina.sh", "run"]
