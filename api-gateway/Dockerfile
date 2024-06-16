
FROM khipu/openjdk17-alpine
LABEL maintainer="Flavio Lionel Rita <flaviolrita@proton.me>"
LABEL description="Api gateway for the cross training services"

WORKDIR /app
COPY app.jar app.jar
EXPOSE 8080
CMD ["sh", "-c", "java -jar app.jar"]