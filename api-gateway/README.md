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

## References

- [tutorial](https://www.youtube.com/watch?v=0N59T8blTkQ&list=PLxy6jHplP3Hi_W8iuYSbAeeMfaTZt49PW&index=16)
