# Register application on Spring Eureak server using Spring Boot

The purpose of this project is to 
1. create a simple shopping application which contains payment-service and amazon-shopping services
2. register the application on Spring Cloud Eureka server using Eureak registry service
3. access microservices using RESTful APIs

## Application Architecture

<img src="https://github.com/kmjenniferng/java-spring-boot-microservices-eureka/blob/main/screenshot-1.png">

As we see from the above diagram, amazon-server acts as Spring Cloud Eureka server. amazon-shopping and payment-service are microservices that we want to deploy on Spring Cloud Eureka server.

### 1. payment-service
In this payment service, we implement a RESTful API called payNow and this API will return "payment with {price} is successful"

localhost:8888/payment-provider/payNow/{price}

### 2. amazon-shopping
In this shopping service, we implement a RESTful API called amazon-payment and this API will invoke payNow API from payment service

localhost:9999/amazon-payment/{price}

### 3. amazon-server
After we deploy our application, we should see payment-service and amazon-shopping are registered on Spring Cloud Eureka server

<img src="https://github.com/kmjenniferng/java-spring-boot-microservices-eureka/blob/main/screenshot-3.png">


## Instructions on running tests using POSTMAN
### Invoke amazon-payment API

HTTP:GET localhost:9999/amazon-payment/{price}

Headers: Key = Content-Type, Value = application/json

Expected test result: payment with {price} is successful

<img src="https://github.com/kmjenniferng/java-spring-boot-microservices-eureka/blob/main/screenshot-2.png">
