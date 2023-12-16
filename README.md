# Create Spring Boot Project without IDE

## Installation (OSX)

### 1\. Install Java

```bash
brew install java

sudo ln -sfn /opt/homebrew/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk

java --version
openjdk 20.0.1 2023-04-18
OpenJDK Runtime Environment Homebrew (build 20.0.1)
OpenJDK 64-Bit Server VM Homebrew (build 20.0.1, mixed mode, sharing)

export JAVA_HOME="$(/usr/libexec/java_home)"
```

### 2\. Install Maven

```bash
brew install maven

mvn --version
Apache Maven 3.9.2 (c9616018c7a021c1c39be70fb2843d6f5f9b8a1c)
Maven home: /opt/homebrew/Cellar/maven/3.9.2/libexec
Java version: 20.0.1, vendor: Homebrew, runtime: /opt/homebrew/Cellar/openjdk/20.0.1/libexec/openjdk.jdk/Contents/Home
Default locale: en_TW, platform encoding: UTF-8
OS name: "mac os x", version: "12.1", arch: "aarch64", family: "mac"

# repository is at ~/.m2/
```

## Create Spring Boot project

- folder

```bash
mkdir -p spring-boot-init/src/main/java/com/example/demo/
```

- pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>3.0.0</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.example</groupId>
	<artifactId>spring-boot-initial</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>spring-boot-initial</name>
	<description>Demo project for Spring Boot</description>
	<properties>
		<java.version>20</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>
```

- MainApplication.java

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ApplicationContext;

@SpringBootApplication
public class MainApplication {
		public static void main(String[] args) {
		ApplicationContext ctx = SpringApplication.run(MainApplication.class, args);
	}	
}
```

- HelloController.java - first API

```java
package com.example.demo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

	@GetMapping("hello")
	public String index() {
		return "Greetings from Spring Boot!";
	}

}
```

## Compile and run Spring Boot

```bash
Option 1:
mvn spring-boot:run # run in the directory that contains pom.xml

Option 2:
mvn clean package # compile to jar, javac can compile but steps will be more
java -jar xxx.jar # run jar file under /target folder
```

## Test

```java
localhost:8080/hello
```
---
Reference: <https://spring.io/guides/gs/spring-boot/>
