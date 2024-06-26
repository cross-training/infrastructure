# Config Service

## Spring Initializer

- [start](https://start.spring.io/#!type=gradle-project&language=java&platformVersion=3.2.6&packaging=jar&jvmVersion=17&groupId=cloud.crosstraining.devstore&artifactId=config&name=config&description=Demo%20project%20for%20Spring%20Boot&packageName=cloud.crosstraining.devstore.config&dependencies=cloud-config-server,security)

## Gradle

**Build:**

```shell
gradle clean build
```

**Run:**

```shell
gradle bootRun
```

- [catalog](http://localhost:8888/discovery-service/docker)

**Test:**

```shell
curl -u devstore:secr3t  http://localhost:8888/catalog-service/docker
curl http://devstore:secr3t@localhost:8888/catalog-service/local
```

## References

- [tutorial](https://www.youtube.com/watch?v=ydtswONk9TE&list=PLxy6jHplP3Hi_W8iuYSbAeeMfaTZt49PW&index=12)
- [tutorial](https://hackmd.io/@6RRl2AU-S2ydlMVeqlhD7g/SJW0ulcY9)
  - [github](https://github.com/digitallab-academy/ms-course-youtube)
