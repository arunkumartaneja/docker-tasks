FROM openjdk:8-jdk-alpine as builder

COPY *.gradle gradle.* gradlew ./
COPY gradle/ gradle/
RUN ./gradlew --version

COPY . .
RUN ./gradlew build -x test --info

FROM openjdk:8-jre-alpine
COPY --from=builder /build/libs/springboot-jpa-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]