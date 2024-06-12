# Registry Service

## Initialize

- [spring](https://start.spring.io/#!type=gradle-project&language=java&platformVersion=3.2.6&packaging=jar&jvmVersion=17&groupId=cloud.crosstraining.devstore&artifactId=registry&name=registry&description=Demo%20project%20for%20Spring%20Boot&packageName=cloud.crosstraining.devstore.registry&dependencies=cloud-eureka-server,cloud-config-client)

## Gradle

**Build:**

```shell
gradle clean build
```

**Run:**

```shell
gradle bootRun
```

**Test:**

- [registry server](http://localhost:8761)

## Docker

**Build & Push:**

```shell
docker build -t flaviorita/devstore-discovery:latest .
docker push flaviorita/devstore-discovery:latest
```

**Run:**

```shell
docker run -p 8761:8080 -e SPRING_PROFILES_ACTIVE=docker --network=devstore_backend -e CONFIG_SERVICE_URI=http://config-server:9101 -e CONFIG_SERVICE_USERNAME=devstore -e CONFIG_SERVICE_PASSWORD=secr3t -e LOGGING_SERVICE_URI=http://tracing-server:9411 flaviorita/devstore-discovery:latest
```

TODO: no me esta funcionando pero si desde docker-compose

## References

- [tutorial](https://www.youtube.com/watch?v=lJ3-VPzhrFY&list=PLxy6jHplP3Hi_W8iuYSbAeeMfaTZt49PW&index=13)
- [Eureka](https://spring.io/guides/gs/service-registration-and-discovery/)
