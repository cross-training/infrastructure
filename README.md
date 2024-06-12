# Infrastructure

## Tasks

**prerequisites:**

```shell
gem install rake git
```

| Task      | Description                                 | Command               |
|-----------|---------------------------------------------|-----------------------|
| Test      | Run the tests                               | `rake test`           |
| Release   | Create a new release                        | `rake release`        |

## Services

- Infrastructure:
  - [Discovery Server](./service/discovery/README.md): Para el registrar y descubrir los servicios
  - [Config Server](./service/config/README.md): Para la configuración de los servicios
  - [Load Balancer](./service/balancer/README.md): Para el balanceo de carga
  - [Circuit Breaker](./service/circuit-breaker/README.md): Para la tolerancia a fallos
  - [Api Gateway](./service/gateway/README.md): Para la seguridad y el enrutamiento
  - [Log Center](./service/logging/README.md): Para el Monitoreo de los servicios
- Database
  - [PostgreSQL](./services/database/postgresql/README.md)
- Monitoring:
  - Prometheus
  - Grafana
- Tracing:  
  - Zipkin:
- Security:
  - Keycloak:

## Tools

- Ansible:
  - [Install](./tools/ansible/README.md#install)
  - [Create Inventory](./tools/ansible/inventory.ini)
- Flyway:
  - [Install](./tools/flyway/README.md#install)
- Terraform:
- Helm:
- Spring boot 3.2.6

## CI/CD

- [Rakefile](./Rakefile)
- GitHub Actions
  - [Build and Dockerize Services](./.github/workflows/build-and-dockerize-services.yml)

## References

- [Canal de Programación Java](https://www.youtube.com/@luigicode1480/videos)
- [Curso de Microservicios con SpringBoot](https://www.youtube.com/watch?v=80zkdQJ2y4c&list=PLxy6jHplP3Hi_W8iuYSbAeeMfaTZt49PW)
  - [Spring Cloud](https://www.youtube.com/watch?v=80zkdQJ2y4c&list=PLxy6jHplP3Hi_W8iuYSbAeeMfaTZt49PW)
- Monitory:
  - [Prometheus](https://prometheus.io/)
  - [Grafana](https://grafana.com/)
  - [Zipkin](https://zipkin.io/)
  - [Rastreo y Monitoreo - Microservicios con Spring Boot](https://youtube.com/watch?v=doGYvlvmN6s)
  - [Microservicios con Spring Boot: Capítulo 11: Zipkin y Sleuth](https://www.youtube.com/watch?v=wF98ikyyKEI)
- Security:
  - [Keycloak](https://www.keycloak.org/)
  - [Spring Security](https://spring.io/projects/spring-security)
  - [Spring Security OAuth](https://spring.io/projects/spring-security-oauth)
  - [spring security samples](https://github.com/spring-projects/spring-security-samples)
  - Tutorials:
    - [Microservicios con Spring Boot: Capítulo 12: Keycloak (parte 1)](https://www.youtube.com/watch?v=uzou3vdmu9Q)
    - [Microservicios con Spring Boot: Capítulo 13: Keycloak (parte 2)](https://www.youtube.com/watch?v=EYIBO1TOSaE)
- [GitHub Actions](./.github/workflows/README.md)

## Info

- [Spring Cloud Kubernetes](https://docs.spring.io/spring-cloud-kubernetes/reference/getting-started.html)
  - Description:
  - Dependence: spring-cloud-starter-Kubernetes-config
  - [tutorial](https://refactorizando.com/microservicios-spring-cloud-kubernetes/)
  - [Externalizar la configuración de Spring Boot en Kubernetes con ConfigMap](https://refactorizando.com/externalizar-configuracion-spring-boot-kubernetes-configmap/)
