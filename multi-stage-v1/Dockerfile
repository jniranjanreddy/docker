FROM schoolofdevops/maven:spring AS build
WORKDIR /app
COPY . .
RUN mvn package -Dmaven.test.skip
#RUN mvn package -DskipTests

FROM openjdk:8-alpine AS run
#COPY --from=build /app/target/spring-petclinic-1.5.2.BUILD-SNAPSHOT.jar /run/petclinic.jar
COPY --from=build /app/target/spring-petclinic-1.5.2.jar /run/petclinic.jar
EXPOSE 8080
CMD java -jar /run/petclinic.jar