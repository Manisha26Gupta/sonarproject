FROM eclipse-temurin:17-jdk AS builder
WORKDIR /workspace
COPY . .

RUN ./gradlew build


FROM eclipse-temurin:17-jdk
WORKDIR /opt/app
RUN useradd -ms /bin/bash appuser
USER appuser

COPY --from=builder /workspace/build/libs/*.jar /opt/app/app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/opt/app/app.jar"]