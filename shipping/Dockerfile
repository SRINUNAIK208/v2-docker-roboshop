FROM maven:3-eclipse-temurin-21-alpine as builder 
WORKDIR /opt/app 
COPY src ./src
COPY pom.xml .
RUN mvn clean package 

FROM maven:3-eclipse-temurin-21-alpine
WORKDIR /opt/app 
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop 
COPY --from=builder  /opt/app/target/shipping-*.jar  /opt/app/shipping.jar
USER roboshop
CMD ["java", "-jar", "shipping.jar"]