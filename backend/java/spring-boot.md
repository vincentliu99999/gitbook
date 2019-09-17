# Spring Boot

* \*\*\*\*[**Learn**](https://spring.io/projects/spring-boot#learn)\*\*\*\*
* [System Requirements](https://docs.spring.io/spring-boot/docs/2.1.8.RELEASE/reference/html/getting-started-system-requirements.html) Java8~12, Maven 3.3+

```bash
java -version
mvn -v
mvn package # build project
mvn dependency:tree # view dependencies
mvn spring-boot:run # run application
```

## **Spring Initializr**

* \*\*\*\*[**http://start.spring.io**](http://start.spring.io)\*\*\*\*
* **Spring Boot CLI**

```text
brew tap pivotal/tap
brew install springboot
```

## Run Application

[Spring Boot Maven Plugin](https://docs.spring.io/spring-boot/docs/current/maven-plugin/usage.html)

```text
mvn spring-boot:run
mvn package && java -jar target/gs-spring-boot-0.1.0.jar
```

