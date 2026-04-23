FROM gradle:8-jdk21 AS builder
WORKDIR /app
COPY build.gradle settings.gradle ./
COPY src ./src
RUN gradle installDist --no-daemon

FROM openjdk:21-slim
WORKDIR /app
COPY --from=builder /app/build/install/hipstershop .
EXPOSE 9555
ENTRYPOINT ["bin/AdService"]
