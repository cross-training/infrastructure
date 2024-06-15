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

- [discovery service](http://localhost:8761)
- [health](http://localhost:8761/actuator/health)
- [prometheus](http://localhost:8761/actuator/prometheus)
- [info](http://localhost:8761/actuator/info)

## References

- [tutorial](https://www.youtube.com/watch?v=lJ3-VPzhrFY&list=PLxy6jHplP3Hi_W8iuYSbAeeMfaTZt49PW&index=13)
- [Eureka](https://spring.io/guides/gs/service-registration-and-discovery/)
