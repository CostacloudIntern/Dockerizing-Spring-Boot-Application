# define base docker image
#FROM openjdk:17-alpine
#LABEL maintainer="vibhooti.net"
#ADD target/Springboot_Dockerization-0.0.1-SNAPSHOT.jar Springboot_Dockerization.jar
#ENTRYPOINT ["java", "-jar", "Springboot_Dockerization.jar"]


FROM openjdk:17-jdk-alpine as build
WORKDIR /app
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline
COPY . ./
RUN ./mvnw install

FROM openjdk:17-alpine
WORKDIR /app
COPY --from=build /app/target/Springboot_Dockerization-0.0.1-SNAPSHOT.jar /app
CMD ["java", "-jar", "Springboot_Dockerization-0.0.1-SNAPSHOT.jar"]