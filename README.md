Spring Boot HTTPS Demo Project

This is a demo Spring Boot application configured to run over HTTPS using an SSL/TLS certificate.
The project demonstrates how to enable HTTPS locally with a keystore and secure communication.

📌 Features

Spring Boot application secured with HTTPS

Self-signed SSL certificate

Embedded Tomcat configuration

Easy to run locally

Suitable for learning and demo purposes

🛠️ Tech Stack

Java 17+ (or Java 11+)

Spring Boot

Embedded Tomcat

SSL (PKCS12 keystore)

📂 Project Structure
spring-boot-https-demo
├── src
│   ├── main
│   │   ├── java/com/example/demo
│   │   │   └── DemoApplication.java
│   │   └── resources
│   │       ├── application.properties
│   │       └── keystore.jks
├── pom.xml
└── README.md

🔐 Generate SSL Keystore

Generate a self-signed certificate using keytool:

keytool -genkeypair \
  -alias springboot \
  -keyalg RSA \
  -keysize 2048 \
  -storetype PKCS12 \
  -keystore keystore.p12 \
  -validity 3650


You will be prompted to set:

Keystore password

Key password

Certificate details (CN, OU, etc.)

Place the generated keystore.p12 / keystore.jks file in:

src/main/resources/

⚙️ HTTPS Configuration

Update application.properties:

server.port=8443

server.ssl.enabled=true
server.ssl.key-store=classpath:keystore.p12 / keystore.jks
server.ssl.key-store-password=changeit
server.ssl.key-store-type=PKCS12
server.ssl.key-alias=springboot

▶️ Run the Application
Using Maven
mvn spring-boot:run

Using JAR
mvn clean package
java -jar target/spring-boot-https-demo.jar

🌐 Access the Application

Open your browser and visit:

https://localhost:8443

