FROM gradle:8.8-jdk21-alpine AS build
WORKDIR /app
COPY . .
RUN gradle --no-daemon clean bootJar

FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
# If you generate PDFs with fonts, you may want fonts installed:
# RUN apk add --no-cache fontconfig ttf-dejavu
COPY --from=build /app/build/libs/*.jar /app/app.jar
EXPOSE 9004
ENV JAVA_OPTS="-XX:MaxRAMPercentage=75 -XX:+UseZGC -Duser.timezone=UTC"
ENTRYPOINT ["sh","-c","java $JAVA_OPTS -jar /app/app.jar"]
