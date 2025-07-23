# Aprendiendo microservicios

Lista de ejercicios y proyectos practicos de los conceptos de microservicios que voy aprendiendo.

---

## Basico 1: CRUD REST con Spring MVC

**Objetivo:** Montar un microservicio independiente que exponga CRUD sobre una entidad (p.ej. "Producto").

**Tecnologias:** Spring Boot MVC, Spring Data JPA, H2, MapStruct, Lombok.

**Entregables:**
  * Endpoint `/api/products` con GET/POST/PUT/DELETE.
  * OpenAPI v3 + Swagger UI habilitado.
  * README con instrucciones para arrancar (`mvn spring-boot:run`).

**Enlace repositorio:** [https://github.com/Johao-dev/product-rest-api](https://github.com/Johao-dev/product-rest-api)

---

## Basico 2: Microservicios sincronos colaborando

**Objetivo:** Crear dos microservicios ("Cliente" y "Pedido") que se comuniquen via REST.

**Tecnologias:** Spring MVC, RestClient, DTOs, Dockerfile basico

**Entregables:**
  * `client-service` y `order-service` en carpetas separadas.
  * Dockerfiles individuales y `docker-compose.yml` para levantar ambos.
  * Documentacion de flujo: cliente crea pedido con datos de cliente.

**Enlace repositorio:** [https://github.com/Johao-dev/learning-microservices-second-exercise](https://github.com/Johao-dev/learning-microservices-second-exercise)

---

## Intermedio 1: API Gateway + Service Discovery

**Objetivo:** Envolver los dos servicios anteriores tras un Gateway y registrar ambos en Eureka.

**Tecnologias:** Spring Cloud Gateway (WebFlux), Spring Cloud Netflix Eureka.

**Entregables:**
  * Gateway con rutas a `/clients/**`, `/orders/**`.
  * Eureka Server + clientes registrados.
  * Pruebas de resiliencia: apagar un servicio y ver fallback simple.

**Enlace repositorio:** [Aun no implementado](https://github.com/Johao-dev/learning-microservices)

---

## Intermedio 2: Config Server + Profiles dinamicos

**Objetivo:** Centralizar configuracion en Git y cambiar propiedades por perfil.

**Tecnologias:** Spring Cloud Config Server, Git loca, `@ConfigurationProperties`.

**Entregables:**
  * Repo (`config-repo`) con `application-dev.yml` y `application-prod.yml`.
  * Services leyendo su configuracion remota.
  * Cambio de perfil en Gateway sin recompilar.

**Enlace repositorio:** [Aun no implementado](https://github.com/Johao-dev/learning-microservices)

---

## Intermedio 3: Observabilidad con Actuator + ELK

**Objetivo:** Instrumentar logs, metricas y expositional health endpoints.

**Tecnologias:** Spring Boot Actuator, Logback JSON, Elasticsearch, Logstash, Kibana (Docker).

**Entregables:**
  * Logs en formato JSON con correlationalId.
  * Stack ELK dockerizado; visualizar logs y metricas de un request.
  * Endpoint `/actuator/metrics` y dashboards basicos en Kibana.

**Enlace repositorio:** [Aun no implementado](https://github.com/Johao-dev/learning-microservices)

---

## Avanzado 1: Resiliencia (Circuit Breaker / Retry)

**Objetivo:** Añadir tolerancia a fallos en llamadas entre servicios.

**Tecnologias:** Resilience4j (Circuit Breaker, Retry), RestClient

**Entregables:**
  * Configurar Circuit Breaker con umbrales de fallo.
  * Probar retry + fallback en un endpoint de prueba.
  * README con pruebas manuales de fallo (curl + logs).

**Enlace repositorio:** [Aun no implementado](https://github.com/Johao-dev/learning-microservices)

---

## Avanzado 2: Comunicacion asincrona con Kafka

**Objetivo:** Sustituir comunicacion directa por eventos en kafka.

**Tecnologias:** Spring for Apache Kafka, Docker-Compose Kafka + Zookeeper

**Entregables:**
  * Publicar evento `OrderCreated` desde `order-servie`
  * `notification-service` que consume evento y envia (simula) email.
  * Scripts para levantar topic, producir y consumir mensajes.

**Enlace repositorio:** [Aun no implementado](https://github.com/Johao-dev/learning-microservices)

---

## Avanzado 3: Patrones CQRS + Event Sourcing

**Objetivo:** Implementar un pequeño CQRS con Event Sourcing para un agregado simple.

**Tecnologias:** Axon Framework (opcional) o implementacion manual, MongoDB para eventos.

**Entregables:**
  * Comandos vs. Queries en servicios separados.
  * Persistencia de eventos en una coleccion "events".
  * Proyeccion de estado actual en otra coleccion.

**Enlace repositorio:** [Aun no implementado](https://github.com/Johao-dev/learning-microservices)

---

## Experto 1: Seguridad distribuida (JWT/OAuth2)

**Objetivo:** Proteger endpoints y propagar claims entre servicios.

**Tecnologias:** Spring Security, JWT, (opcional) Spring Authorization Server o Keycloak.

**Entregables:**
  * Gateway valida token y propaga usuario a downstream.
  * Servicios usan `@PreAuthorize` segun roles.
  * Scripts para generar tokens de prueba.

**Enlace repositorio:** [Aun no implementado](https://github.com/Johao-dev/learning-microservices)

---

## Experto 2: Despliegue en Kubernetes + CI/CD basico

**Objetivo:** Orquestar todo en K8s local (Minikube o Kind) y montar pipeline.

**Tecnologias:** Kubernetes (Deployment, Service, Ingress), Helm (opcional), GitHub Actions.

**Entregables:**
  * Manifiestos YAML para cada microservicio + Gateway + Kafka + ELK + Zipkin.
  * Pipeline que build-ea, push-ea imagenes a Docker Hub y despliega en K8s.
  * README con pasos de despliegue y evidencias (screenshots logs).

**Enlace repositorio:** [Aun no implementado](https://github.com/Johao-dev/learning-microservices)

---

## Formato de entrega para cada ejercicio

1. **README** claro: descripcion, diagrama, pasos de setup y demo.
2. **Swagger/OpenAPI** documentado.
3. **Docker Compose o Kubernetes manifests** segun corresponda.
4. **Capturas de pantalla o grapaciones cortas** que muestren la aplicacion en funcionamiento.