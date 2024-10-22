# Kafka Event-Driven Microservices Architecture with Spring Boot
## Overview
This project demonstrates a Kafka-based event-driven microservices architecture using Spring Boot. It enables communication between microservices via Kafka topics, ensuring decoupled, scalable, and asynchronous message processing.

## Key Features
- Apache Kafka: Acts as a message broker to enable communication between microservices.
- Spring Boot: Provides a robust framework for building microservices.
- Event-Driven Architecture: Utilizes Kafka topics for asynchronous communication.
  
## Prerequisites
Before starting the project, ensure the following software is installed on your machine:
- <b>JDK:</b> Java Development Kit version 17 or higher. <br>To verify your JDK installation:
```bash
java -version
```
- <b>Maven:</b> Apache Maven version 3.8.1 or higher. To verify Maven installation:
```bash
mvn -version
```
- <b>Spring Boot:</b> Spring Boot version 3.0.0 or higher (configured via Maven dependencies in the pom.xml).
- <b>Kafka:</b> Apache Kafka version 3.7.1 or higher.
- <b>ZooKeeper:</b> Comes packaged with Kafka; used for managing Kafka brokers.

  
## Getting Started
1. <b>Clone the Repository:</b>
```bash
git clone <repository-url>
```
2. <b>Start ZooKeeper:</b> Kafka uses ZooKeeper to manage the brokers. To start ZooKeeper, navigate to the Kafka installation directory and run
```bash
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```
<b><i>This starts ZooKeeper on the default port 2181</i></b>

3. <b>Start Kafka Broker:</b> After ZooKeeper is up and running, start the Kafka broker 
```bash
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

<b><i>This starts Kafka on port 9092 (default). Ensure that both ZooKeeper and Kafka are running correctly before moving forward.</i></b>

### Project Setup
1. <b>Build the Spring Boot Application:</b> To build the Spring Boot microservices, run the following Maven command from the root of your project
```bash
mvn clean install
```
2. <b>Configure Kafka in Spring Boot:</b> Ensure the following properties are set in your Spring Boot application’s application.properties or application.yml file:
   #### Kafka properties
   - `spring.kafka.bootstrap-servers=localhost:9092`
   - `spring.kafka.consumer.group-id=group_id`
   - `spring.kafka.consumer.auto-offset-reset=earliest`
   - `spring.kafka.producer.key-serializer=org.apache.kafka.common.serialization.StringSerializer`
   - `spring.kafka.producer.value-serializer=org.springframework.kafka.support.serializer.JsonSerializer`
   - `spring.kafka.consumer.key-deserializer=org.apache.kafka.common.serialization.StringDeserializer`
   - `spring.kafka.consumer.value-deserializer=org.springframework.kafka.support.serializer.JsonDeserializer` <br>
3. <b>Running the Application:</b> To start the Spring Boot microservices, use the following command
```bash
mvn spring-boot:run
```

<b><i>Each microservice will connect to Kafka for producing or consuming messages, based on the configuration provided.</i></b>

## Version Information
- JDK Version: 17 or higher
- Maven Version: 3.8.1 or higher
- Spring Boot Version: 3.0.0 or higher
- Kafka Version: 3.7.1 or higher
- ZooKeeper Version: Bundled with Kafka

## Troubleshooting
- Kafka Broker not connecting: Ensure ZooKeeper is running and Kafka is correctly configured to use localhost:9092.
- Message Not Consumed: Check consumer group ID and ensure the topic is correctly set in the application properties.
  
## Conclusion
This documentation provides the necessary steps to set up a Kafka event-driven microservices architecture using Spring Boot. The project demonstrates how to produce and consume messages asynchronously, promoting loose coupling between services.
