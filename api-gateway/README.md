# Gateway Service

## Initialize

- [spring](https://start.spring.io/#!type=gradle-project&language=java&platformVersion=3.2.6&packaging=jar&jvmVersion=17&groupId=cloud.crosstraining.devstore&artifactId=gateway&name=gateway&description=Demo%20project%20for%20Spring%20Boot&packageName=cloud.crosstraining.devstore.gateway&dependencies=cloud-config-client,cloud-gateway,cloud-eureka)

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

- [health](http://localhost:8080/actuator/health)
- [prometheus](http://localhost:8080/actuator/prometheus)
- [info](http://localhost:8080/actuator/info)

## Docker

**Build & Push:**

```shell
docker build -t flaviorita/devstore-gateway:latest .
docker push flaviorita/devstore-gateway:latest
```

**Run:**

```shell
docker run -p 8080:8080 --network=devstore_backend -e SPRING_PROFILES_ACTIVE=docker -e DISCOVERY_SERVICE_URI=http://discovery-server:8761/eureka/ -e CONFIG_SERVICE_URI=http://config-server:8888 -e CONFIG_SERVICE_USERNAME=devstore -e CONFIG_SERVICE_PASSWORD=secr3t flaviorita/devstore-gateway:latest
```

## References

- [tutorial](https://www.youtube.com/watch?v=0N59T8blTkQ&list=PLxy6jHplP3Hi_W8iuYSbAeeMfaTZt49PW&index=16)