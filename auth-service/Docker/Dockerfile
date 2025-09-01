# ---------- Build stage ----------
FROM gradle:8.8-jdk21-alpine AS build
WORKDIR /app
COPY . .
RUN gradle --no-daemon clean bootJar

# ---------- Runtime stage ----------
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
# (Optional) add CA certs or tzdata if needed:
# RUN apk add --no-cache tzdata
COPY --from=build /app/build/libs/*.jar /app/app.jar
EXPOSE 9000
ENV JAVA_OPTS="-XX:MaxRAMPercentage=75 -XX:+UseZGC -Duser.timezone=UTC"
ENTRYPOINT ["sh","-c","java $JAVA_OPTS -jar /app/app.jar"]
