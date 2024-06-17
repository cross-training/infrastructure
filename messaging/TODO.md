# Messaging Service

En Spring Boot y Spring Cloud, existen varias opciones para implementar un servicio que gestione la mensajería a través de varios canales como email, SMS, etc. A continuación, te menciono algunas de las opciones más comunes y prácticas:

## Spring Cloud Stream

Spring Cloud Stream es un marco de trabajo que permite crear aplicaciones de microservicios que se comunican a través de sistemas de mensajería. Puedes utilizarlo junto con diferentes sistemas de mensajería como Kafka, RabbitMQ, etc. Para manejar distintos canales como email y SMS, puedes crear bindings específicos para cada tipo de mensaje.

## Spring Integration

Spring Integration proporciona un framework de integración ligero que te permite construir aplicaciones de integración mediante el uso de Enterprise Integration Patterns (EIP). Puedes configurar canales para email y SMS utilizando adaptadores de correo electrónico y SMS.

## Twilio

Twilio es una plataforma de comunicación en la nube que ofrece APIs para SMS, voz, video, email, y más. Puedes integrar Twilio en una aplicación Spring Boot utilizando sus bibliotecas y servicios RESTful.

## SendGrid

SendGrid es una plataforma de email marketing y transaccional que ofrece APIs para enviar emails y gestionar campañas de email. Puedes integrar SendGrid en una aplicación Spring Boot utilizando sus bibliotecas y servicios RESTful.

## Ejemplo de Implementación

A continuación, te muestro un ejemplo de cómo implementar un servicio de mensajería en Spring Boot utilizando Spring Cloud Stream y RabbitMQ:

1. Agrega las dependencias de Spring Cloud Stream y RabbitMQ en tu archivo `build.gradle`:

```gradle

dependencies {
    implementation 'org.springframework.cloud:spring-cloud-starter-stream-rabbit'
    implementation 'org.springframework.boot:spring-boot-starter-web'
}

```

1. Configura la conexión a RabbitMQ en tu archivo `application.properties`:

```properties

spring.cloud.stream.bindings.output.destination=myQueue
spring.rabbitmq.host=localhost
spring.rabbitmq.port=5672
spring.rabbitmq.username=guest
spring.rabbitmq.password=guest

```

1. Crea un controlador REST para enviar mensajes a RabbitMQ:

```java

@RestController
public class MessageController {

    @Autowired
    private Source source;

    @PostMapping("/send")
    public void sendMessage(@RequestBody String message) {
        source.output().send(MessageBuilder.withPayload(message).build());
    }
}

```

1. Crea un consumidor de mensajes para procesar los mensajes enviados a RabbitMQ:

```java

@EnableBinding(Sink.class)
public class MessageConsumer {

    @StreamListener(Sink.INPUT)
    public void handleMessage(String message) {
        System.out.println("Received message: " + message);
    }
}

```

Con estos pasos, has configurado un servicio de mensajería en Spring Boot que envía y recibe mensajes a través de RabbitMQ. Puedes adaptar este ejemplo para implementar otros canales de mensajería como email y SMS utilizando las bibliotecas y servicios adecuados.

## Ejemplo con Twilio

### Configuración para enviar mensajes SMS con Twilio en Spring Boot

#### Paso 1: Configurar dependencias en `pom.xml`

```xml
<dependencies>
    <dependency>
        <groupId>com.twilio.sdk</groupId>
        <artifactId>twilio</artifactId>
        <version>8.25.0</version>
    </dependency>
</dependencies>
```

#### Paso 2: Configurar las credenciales de Twilio en `application.properties`

```properties
twilio.account.sid=YOUR_ACCOUNT_SID
twilio.auth.token=YOUR_AUTH_TOKEN
twilio.phone.number=YOUR_TWILIO_PHONE_NUMBER
```

#### Paso 3: Configurar Twilio en una clase de configuración

```java
import com.twilio.Twilio;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class TwilioConfig {

    @Value("${twilio.account.sid}")
    private String accountSid;

    @Value("${twilio.auth.token}")
    private String authToken;

    @Bean
    public void initializeTwilio() {
        Twilio.init(accountSid, authToken);
    }
}
```

#### Paso 4: Implementar un servicio para enviar SMS

```java
import com.twilio.rest.api.v2010.account.Message;
import com.twilio.type.PhoneNumber;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class SmsService {

    @Value("${twilio.phone.number}")
    private String twilioPhoneNumber;

    public void sendSms(String to, String body) {
        Message.creator(
            new PhoneNumber(to),
            new PhoneNumber(twilioPhoneNumber),
            body
        ).create();
    }
}
```

#### Paso 5: Utilizar el servicio en un controlador

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/sms")
public class SmsController {

    private final SmsService smsService;

    @Autowired
    public SmsController(SmsService smsService) {
        this.smsService = smsService;
    }

    @PostMapping("/send")
    public void sendSms(@RequestParam String to, @RequestParam String message) {
        smsService.sendSms(to, message);
    }
}
```

## Referencias

- [Spring Cloud Stream](https://spring.io/projects/spring-cloud-stream)
- [Spring Integration](https://spring.io/projects/spring-integration)
- [Twilio](https://www.twilio.com/)
- [SendGrid](https://sendgrid.com/)
- [RabbitMQ](https://www.rabbitmq.com/)
- [Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/)
- [Messaging Patterns](https://www.enterpriseintegrationpatterns.com/patterns/messaging/)
- [Spring Cloud Stream with RabbitMQ](https://spring.io/guides/gs/messaging-rabbitmq/)
- [Spring Integration Reference Guide](https://docs.spring.io/spring-integration/reference/html/)
- [Twilio Java Library](https://www.twilio.com/docs/libraries/java)
