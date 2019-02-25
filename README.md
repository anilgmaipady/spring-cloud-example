[[TOC]]

# Centralized Configuration

![image alt text](image_0.png)

Code - [https://github.com/anilgmaipady/spring-cloud-example/tree/master/spring-cloud-config-server](https://github.com/anilgmaipady/spring-cloud-example/tree/master/spring-cloud-config-server)

* Configuration seperated from code and centralized.

* Changes are pushed to all servcies without servcei restart.

# **Servcie Discovery Load Balancer API Gateway**

![image alt text](image_1.png)

All servcies registres them self with naming server.

![image alt text](image_2.png)

Ribbon - Client side load balancer 

[https://github.com/anilgmaipady/spring-cloud-example/tree/master/currency-conversion-service](https://github.com/anilgmaipady/spring-cloud-example/tree/master/currency-conversion-service)

Eureka - Servcie registry ( Naming server )

[https://github.com/anilgmaipady/spring-cloud-example/tree/master/netflix-eureka-naming-server](https://github.com/anilgmaipady/spring-cloud-example/tree/master/netflix-eureka-naming-server)

Zuul - API Gateway

[https://github.com/anilgmaipady/spring-cloud-example/tree/master/netflix-zuul-api-gateway-server](https://github.com/anilgmaipady/spring-cloud-example/tree/master/netflix-zuul-api-gateway-server)

# **Aplication Performance Monitoring Using micrometer and prometheus**

* All services exposes /actuator/prometheus REST end points.

*  Prometheus stores and exposes time series metrics for visualization frameworks.

* [https://micrometer.io/](https://micrometer.io/)

* [https://prometheus.io/](https://prometheus.io/)

# **Distributed Tracing**

Code is part of the servcies:

[https://github.com/anilgmaipady/spring-cloud-example/tree/master/currency-conversion-service](https://github.com/anilgmaipady/spring-cloud-example/tree/master/currency-conversion-service)

[https://github.com/anilgmaipady/spring-cloud-example/tree/master/currency-exchange-service](https://github.com/anilgmaipady/spring-cloud-example/tree/master/currency-exchange-service)

* [https://zipkin.io/](https://zipkin.io/)

* [https://www.rabbitmq.com/](https://www.rabbitmq.com/)

## Frameworks Used

* Servcies send traces to rabit MQ

* Zipkin provied trace storage and retrival.

* Rabit MQ/Zipkin  can be reaplces with other similar frameworks.

![image alt text](image_3.png)

## Spring Boot Admin

* Administration app for spring based micro servcies.

* Details - [https://github.com/codecentric/spring-boot-admin](https://github.com/codecentric/spring-boot-admin)

* Code - [https://github.com/anilgmaipady/spring-cloud-example/tree/master/netflix-eureka-naming-server](https://github.com/anilgmaipady/spring-cloud-example/tree/master/netflix-eureka-naming-server)

## Frameworks Used

### **Eureka**

Eureka used for locating services for the purpose of load balancing and failover of middle-tier servers

### **Zuul**

Zuul uses a range of different types of filters that enables us to quickly and nimbly apply functionality to our edge service. These filters help us perform the following functions:

* Authentication and Security - identifying authentication requirements for each resource and rejecting requests that do not satisfy them.

* Insights and Monitoring - tracking meaningful data and statistics at the edge in order to give us an accurate view of production.

* Dynamic Routing - dynamically routing requests to different backend clusters as needed.

* Stress Testing - gradually increasing the traffic to a cluster in order to gauge performance.

* Load Shedding - allocating capacity for each type of request and dropping requests that go over the limit.

* Static Response handling - building some responses directly at the edge instead of forwarding them to an internal cluster

* Multiregion Resiliency - routing requests across AWS regions in order to diversify our ELB usage and move our edge closer to our members

### **Feign**

Feign is a java to http client binder inspired by [Retrofit](https://github.com/square/retrofit), [JAXRS-2.0](https://jax-rs-spec.java.net/nonav/2.0/apidocs/index.html), and [WebSocket](http://www.oracle.com/technetwork/articles/java/jsr356-1937161.html). Feign's first goal was reducing the complexity of binding [Denominator](https://github.com/Netflix/Denominator) uniformly to http apis regardless of [restfulness](http://www.slideshare.net/adrianfcole/99problems).

### **Ribbon**

Ribbon is a client side IPC library that is battle-tested in cloud. It provides the following features

* Load balancing

* Fault tolerance

* Multiple protocol (HTTP, TCP, UDP) support in an asynchronous and reactive model

* Caching and batching

### **Hystrix **

* Give protection from and control over latency and failure from dependencies accessed (typically over the network) via third-party client libraries.

* Stop cascading failures in a complex distributed system.

* Fail fast and rapidly recover.

* Fallback and gracefully degrade when possible.

* Enable near real-time monitoring, alerting, and operational control

### Zipkin

* [https://zipkin.io/](https://zipkin.io/)

### Prometheus

* [https://prometheus.io/](https://prometheus.io/)

# Runing the Code

## Installing Rabbit MQ

### Windows

https://www.rabbitmq.com/install-windows.html

https://www.rabbitmq.com/which-erlang.html

http://www.erlang.org/downloads

Video - https://www.youtube.com/watch?v=gKzKUmtOwR4

### Mac

https://www.rabbitmq.com/install-homebrew.html

## Setting up Distributed Tracing with Zipkin

Quick Start Page:

https://zipkin.io/pages/quickstart

Downloading Zipkin Jar:

https://search.maven.org/remote_content?g=io.zipkin.java&a=zipkinserver&

v=LATEST&c=exec

### Command to run

RABBIT_URI=amqp://localhost java -jar zipkin-server-2.5.2-

Exec.jar

## Setup Prometheus

[https://prometheus.io/docs/prometheus/latest/getting_started/](https://prometheus.io/docs/prometheus/latest/getting_started/)

## Start Servcies

Clone code  - [https://github.com/anilgmaipady/spring-cloud-example](https://github.com/anilgmaipady/spring-cloud-example)

Got to following sub directories and start servceis in the following order using the command:

**mvn spring-boot:run &**

**Servcie order:**

spring-cloud-config-server

Netflix-eureka-naming-server

Netflix-zuul-api-gateway-server

Limits-service

Currency-exchange-service

currency-conversion-service

# Screen shots

## Spring Boot Admin

![image alt text](image_4.png)

![image alt text](image_5.png)

![image alt text](image_6.png)

![image alt text](image_7.png)

## Distributed Trace

### Servcie Depencency

![image alt text](image_8.png)

### Find distributed trace

![image alt text](image_9.png)

### Drill down a HTTP trace ![image alt text](image_10.png)

## APM Using Prometheus

![image alt text](image_11.png)

