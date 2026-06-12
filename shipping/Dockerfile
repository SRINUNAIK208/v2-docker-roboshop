FROM maven:3-eclipse-temurin-21-alpine as builder 
WORKDIR /opt/app 
COPY src ./src
COPY pom.xml .
RUN mvn clean package 
RUN mv target/shipping-*.jar shipping.jar

FROM maven:3-eclipse-temurin-21-alpine
WORKDIR /opt/app 
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop 
COPY --from=builder --chown=roboshop:roboshop /opt/app/shipping.jar .
USER roboshop
CMD ["java", "-jar", "shipping.jar"]