# Code conventions followed in [Rokomari.com](https://www.rokomari.com)

---

# Table of Contents

- [Naming Conventions](https://github.com/rokomari-com/convention/blob/master/README.md#naming-conventions) : Describe various programming naming schema (ex: variable, method names etc)
  - [Package Naming](https://github.com/rokomari-com/convention/blob/master/README.md#package-naming)
  - [Class Naming](https://github.com/rokomari-com/convention/blob/master/README.md#class-naming)
  - [Interface Naming](https://github.com/rokomari-com/convention/blob/master/README.md#interface-naming)
  - [Method Naming](https://github.com/rokomari-com/convention/blob/master/README.md#method-naming)
  - [Variable Naming](https://github.com/rokomari-com/convention/blob/master/README.md#variable-naming)
  - [Constant Naming](https://github.com/rokomari-com/convention/blob/master/README.md#constant-naming)
  - [Abstract Class Naming](https://github.com/rokomari-com/convention/blob/master/README.md#abstract-class-naming)
  - [Exception Class Naming](https://github.com/rokomari-com/convention/blob/master/README.md#exception-class-naming)
  - [Enum Member Naming](https://github.com/rokomari-com/convention/blob/master/README.md#enum-member-naming)
  - [Generic Type Naming](https://github.com/rokomari-com/convention/blob/master/README.md#generic-type-naming)
  - [Annotation Naming](https://github.com/rokomari-com/convention/blob/master/README.md#annotation-naming)
  - [Unit Test Class Naming](https://github.com/rokomari-com/convention/blob/master/README.md#unit-test-class-naming)
  - [Integration Test Class Naming](https://github.com/rokomari-com/convention/blob/master/README.md#integration-test-class-naming)
  - [Test Method Naming](https://github.com/rokomari-com/convention/blob/master/README.md#test-method-naming)

- [Base Conventions](https://github.com/rokomari-com/convention/blob/master/README.md#base-conventions) : Descibe the basic coding conventions.
  - [Copyright Text](https://github.com/rokomari-com/convention/blob/master/README.md#copyright-text)
  - [Code Block](https://github.com/rokomari-com/convention/blob/master/README.md#code-block)
  - [Braces](https://github.com/rokomari-com/convention/blob/master/README.md#braces-)
  - [Parentheses](https://github.com/rokomari-com/convention/blob/master/README.md#parentheses-)
  - [Operator](https://github.com/rokomari-com/convention/blob/master/README.md#Operator)
  - [Control Statement](https://github.com/rokomari-com/convention/blob/master/README.md#control-statement)
  - [Variable](https://github.com/rokomari-com/convention/blob/master/README.md#variable)
  - [Class](https://github.com/rokomari-com/convention/blob/master/README.md#class)

- [Java Conventions](https://github.com/rokomari-com/convention/blob/master/README.md#java-conventions) : Describe the **JAVA** programming language conventions

- [Spring Conventions](https://github.com/rokomari-com/convention/blob/master/README.md#spring-conventions) : Describe the **Spring Framework** project related conventions.
  - [Project Bootstrap](https://github.com/rokomari-com/convention/blob/master/README.md#project-bootstrap)
  - [Api Design Guide](https://github.com/rokomari-com/convention/blob/master/README.md#api-design-guide)
  - [Application Architecture](https://github.com/rokomari-com/convention/blob/master/README.md#application-architecture)
  - [Application Properties](https://github.com/rokomari-com/convention/blob/master/README.md#application-properties)
  - [Application Folder Structure](https://github.com/rokomari-com/convention/blob/master/README.md#application-folder-structure)
  - [Banner](https://github.com/rokomari-com/convention/blob/master/README.md#banner)
  - [Copyright Text](https://github.com/rokomari-com/convention/blob/master/README.md#copyright-text)
  - [Database](https://github.com/rokomari-com/convention/blob/master/README.md#database)
  - [Datatype](https://github.com/rokomari-com/convention/blob/master/README.md#datatype)
  - [Docker](https://github.com/rokomari-com/convention/blob/master/README.md#docker)
  - [File and Method Naming](https://github.com/rokomari-com/convention/blob/master/README.md#file-and-method-naming)
  - [General Convention](https://github.com/rokomari-com/convention/blob/master/README.md#general-convention)
  - [Hibernate](https://github.com/rokomari-com/convention/blob/master/README.md#hibernate)
  - [Port Arrangement](https://github.com/rokomari-com/convention/blob/master/README.md#port-arrangement)
  - [View Layer](https://github.com/rokomari-com/convention/blob/master/README.md#view-layer)

---

# Naming Conventions

## Package Naming
- should be noun
- should be all `lowercase`
- should be only one word after each dot
- only use English words, avoid especial characters (`_` /`$` etc)
```java
package com.rokomari.model
```

## Class Naming
- should be noun
- should be `UpperCammelCase`
- should bound the namming upto 2 words
- should not start/end with `_` / `$`
- for domain classes, use `UPERCASE` domain part postfix. (Ex: `RefundDTO` instead of ~~RefundDto~~)
- if any ***Design Pattern*** used, should add the patterns name in the postfix. (Ex: `CustomerObserver`, `ItemObservable`, `CakeFactory`)
- avoid uncommon abbreviations in naming. (Ex: use `AbstractCake` instead of ~~AbsCake~~)
```java
public class CompanyService {
    ...
}
```

## Interface Naming
- should be `UpperCammelCase`
- should be Adjective, Ex: `Eatable`
- can be noun if the interface marked as parent class (Ex: `LocationService`) or presented as a family of classes (Ex: `List`, `Map`)
- should not start/end with `_` / `$`
```java
public interface Focusable {
    ...
}
```

## Method Naming
- should be verb, like giving a command/action
- should be `lowerCammelCase`
- should contains upto highest 3 params. If required > 3 params, params should wrap around into a model and pass.
- if the language support named params, priotize them.
- should be bound upto 3 words
- should not start/end with `_` / `$` (exception for `_` if language required `_` for private modification)
- avoid writting `Boolean` veriable's `getter/setter` using `is`. use `getValue()/setValue()`. (Ex: `void setCompleted(Boolean boolean)`, `Boolean getCompleted()`)
```java
List<User> getAllUsers(Integer id) {
    ...
}
```

## Variable Naming
- should be noun
- should be in `lowerCammelCase`
- should bound upto 2 words
- should not start/end with `_` / `$` (exception for `_` if language required `_` for private modification)
- avoid using `is` prefix for `Boolean` data type. (Ex: use `completed` instead of ~~isComplete~~ / ~~isCompleted~~ )
```java
String firstName;
```

## Constant Naming
- should be `UPPERCASE` with `UNDER_SCORE` between words
- should be noun
- should bound upto 2 words
- should not start/end with `_` / `$`
```java
private Double MAX_PRICE == 99.0D;
```

## Abstract Class Naming
- same as `class` naming convention, but has `Base` / `Abstract` prefix
```java
abstract class BaseActivity {
    ...
}
```

## Exception Class Naming
- same as `class` naming convention, but has `Exception` postfix
```java
public class MessageNotFoundException extends Exception {
    ...
}
```

## Enum Member Naming
- should be noun
- should be `UPPERCASE` with `UNDER_SCORE` between words
- upto 2 words
```java
public enum Status {
    NOT_COMPLETE,
    COMPLETE
}
```

## Generic Type Naming
- `T` for general purpose use
- `E` for collection elements
- `K` & `V` for key-value pair
```java
public interface StudentMap<K,V> {
    ....
}
```

## Annotation Naming
- should be `UpperCammelCase`
- can be noun/adjective/verb based on use-case
```java
public @interface EnableCaching

public @interface Depricated
```

## Unit Test Class Naming
- should follow `class-under-test`'s package structure for the test class
- name should be same as `class-under-test`'s name with `Test` postfix
```java
public class TransactionTest {
    ...
}
```

### Integration Test Class Naming
- should follow `class-under-test`'s package structure for the test class
- name should be same as `class-under-test`'s name with `IntegTest` postfix
```java
public class TransactionIntegTest {
    ...
}
```

### Test method Naming
- method name breaks down into `4` sections. (`method-under-test`, `GIVEN block`[Optinal], `WHEN block`, `THEN block`). each block should follow `lowerCammelCase` & between them should have `under_score`.
- `GIVEN`,`WHEN`,`THEN` blocks should prefix with respective type names.
- `GIVEN` block describe the precondition of the test.
- `WHEN` block describe the condition of the test.
- `THEN` block describe the desired output of the test.
```java
@Test
void getAllUsers_givenDBAccessFailure_whenDBReturnEmpty_thenShouldReturnEmptyList() {
    ...
}
```

--- 

# Base Conventions

## Copyright Text

- Add copyright text in the start of every file. For example :

        Copyright (c), Onnorokom Web Services Ltd (OWSL) and/or its affiliates. All rights reserved.
        OWSL PROPRIETARY/CONFIDENTIAL. Use is subject to license terms.

## Code Block
- use `4` spaces for block indentation.
- Use a single blank line to separate sections with the same logic or semantics.

## Braces `{}`
- A space before opening brace.
- No line break before the opening brace.
- Line break after the opening brace.
- Line break before the closing brace.
- Line break after the closing brace, only if that brace terminates a statement or terminates the body of a method, constructor, or named class. For example, there is no line break after the brace if it is followed by else or a comma.
```java
return () -> {
    while (condition()) {
        method();
    }
};

class MyClass() {

    @Override
    public void method() {
        if (condition()) {
            try {
                something();
            } catch (ProblemException e) {
                recover();
            }
        } else if (otherCondition()) {
            somethingElse();
        } else {
            lastThing();
        }
    }
}
```
- always use braces for single-line blocks.
    ```java
    if (condition()) {
        statement();
    } 
    ```
- for empty blocks, block should be closed in the next line.
  ```java
  if (condition()) {
  }
  ```

## Parentheses `()`
- No space is used between the `(` character and its following character. Same for the `)` character and its preceding character.
  ```java
  void statement(Integer i) {
      ...
  }
  ```
- if method has multiple parameters, their should be a space between them in the method declaration & metthod calling
  ```java
  void statement(Integer i, String st, Status status) {
      ...
  }

  statement(1, "Hello", Status.FINISHED);
  ```
- There must be one space between keywords, such as if/for/while/do/switch/try/catch/finally etc, and parentheses.
---

## Operator
- There must be one space at both left and right side of operators, such as `=`, `&&`, `+`, `-`, ternary operator, etc.
  ```java
  Integer i = 10;
  Boolean b = false;
  if (i == 10 && b == true) {
      i = i + 1 ? 0 : -10;
      i++;
  }
  ```

## Control Statetment
- In a `switch` block, each case should be finished by *break/return*. If not, a note should be included to describe at which case it will stop. Within every `switch` block, a default statement must be present, even if it is empty.

## Variable
- avoid using premitive data type if the language provide equivalent reference type. (Ex: for **Java** use `Integer` instead of ~~int~~)
- for Array, use `[]` after type, instead of variable name. (Ex: use `String[] names;` instead of ~~String names[]~~ )
- for `Long` value use `L` instead of ~~l~~, & for `Double` value use `D` instead of ~~d~~. use these literals when ever possible.
- if language supports, use `under_score` between big integer value for easy reading purpose.
    ```java
    Integer money = 1_00_000;
    ```

## Class
- for ***OOP*** languages, every file should contains `1` top level class.
- source file should contains followings **in order**
  1. License or copyright information, if present
  2. Package statement
  3. Import statements
  4. Exactly one top-level class
   
  **Exactly one blank line** separates each section that is present.

- inside the class, following conventions should be followed **in order**
  1. final variables
  2. static variables
  3. public variables (P.S: using getter/setter of a private veriable instead is recommendend)
  4. private variables
  5. static methods
  6. constructors (default constructor at the first)
  7. public methods & thier dependent private methods
  8. inner static class
  9. inner class
  10. supporting enum class

  **Exactly one blank line** separates each section that is present.

  **Exactly one blank line** before first section that is present.

- use different classes for configurations/utilities/constants based on their type. Avoid using one big file for all types. Ex ->
  > wallet related constant should go to WalletConstants.
   Account related constant should go to Account Constansts.

  > Dagger Library config should go to DaggerConfig.
   Swagger Library config should go to SwaggerConfig.

   > Validation related utilities should go to ValidationUtils.
    Convertion related utilities should go to ConvertionsUtils.

---

# Java Conventions

1. **[Mandatory]** An overridden method from an interface or abstract class must be marked with `@Override` annotation.

2. **[Mandatory]** Using a deprecated class or method is prohibited.

3. **[Mandatory]** Since `NullPointerException` can possibly be thrown while calling the *equals* method of `Object`, *equals* should be invoked by a constant or an object that is definitely ot *null*.  
    > Positive example: `"test".equals(object);`
    > Counter example: `object.equals("test");`

4. **[Mandatory]** Use the `equals` method, rather than reference equality `==`, to compare primitive wrapper classes.

5. **[Recommended]** Multiple constructor methods or homonymous methods in a class should be put together for better readability.

6. **[Recommended]** Keyword *final* should be used in the following situations:    
    1) A class which is not allow to be inherited.
    2) A variable which is not allow to be modified.   
    3) A method which is not allow to be overridden.

7. **[Recommended]** Define the access level of members in class with severe  restrictions:    
    1) Constructor methods must be `private` if an allocation using `new` keyword outside of the class is forbidden.   
    2) Constructor methods are not allowed to be `public` or `default` in a utility class.   
    3) Nonstatic class variables that are accessed from inheritants must be `protected`.  
    4) Nonstatic class variables that no one can access except the class that contains them must be `private`.  
    5) Static variables that no one can access except the class that contains them must be `private`.       
    6) Static variables should be considered in determining whether they are `final`.  
    7) Class methods that no one can access except the class that contains them must be `private`.  
    8) Class methods that are accessed from inheritants must be `protected`.   
    > Note: We should strictly control the access for any classes, methods, arguments and variables. Loose access control causes harmful coupling of modules. Imagine the following situations. For a `private` class member, we can remove it as soon as we want. However, when it comes to a `public` class member, we have to think twice before any updates happen to it. 


### Exception

1. **[Mandatory]** Do not catch *Runtime* exceptions defined in *JDK*, such as `NullPointerException` and `IndexOutOfBoundsException`. Instead, pre-check is recommended whenever possible.  
    > Note: Use try-catch only if it is difficult to deal with pre-check, such as `NumberFormatException`.  
    > Positive example: ```if (obj != null) {...}```  
    > Counter example: ```try { obj.method() } catch(NullPointerException e){…}```

2. **[Mandatory]** It is irresponsible to use a try-catch on a big chunk of code. Be clear about the stable and unstable code when using try-catch. The stable code that means no exception will throw. For the unstable code, catch as specific as possible for exception handling.

3. **[Mandatory]** Do not suppress or ignore exceptions. If you do not want to handle it, then re-throw it. The top layer must handle the exception and translate it into what the user can understand.

4. **[Mandatory]** Make sure to invoke the rollback if a method throws an Exception.

5. **[Mandatory]** Closeable resources (stream, connection, etc.) must be handled in *finally* block. Never throw any exception from a *finally* block.  
    > Note: Use the *try-with-resources* statement to safely handle closeable resources (Java 7+).

6. **[Mandatory]** Never use *return* within a *finally* block.

7. **[Recommended]** If a method can return `null`, then wrap the return type of the method with `Optional<Type>`. return `Optional.empty()` instead of `null`.

8. **[Recommended]** Do not throw `RuntimeException`, `Exception`, or `Throwable` directly. It is recommended to use well defined custom exceptions such as `DAOException`, `ServiceException`, etc.

9. **[For Reference]** Avoid duplicate code (Do not Repeat Yourself, also known as DRY principle).  
    > <font color="#977C00">Note: </font>Copying and pasting code arbitrarily will inevitably lead to duplicated code. If you keep logic in one place, it is easier to change when needed. If necessary, extract common codes to methods, abstract classes or even shared modules.

10. **[For Reference]** Try simple solution instead of complex one (Keep It Simple Silly (KISS))


### Logs

1. **[Mandatory]** Do not use API in log system (Log4j, Logback) directly. API in log framework SLF4J is recommended to use instead, which uses *Facade* pattern and is conducive to keep log processing consistent.
    ```java
    import org.slf4j.Logger; 
    import org.slf4j.LoggerFactory;
    private static final Logger logger = LoggerFactory.getLogger(Abc.class); 

    ```

---

# Spring Conventions

## Project Bootstrap

1. Do not use Gradle wrapper. Manually install Gradle in development machine and update it regularly.

1. Use all small letter naming conventions for project naming. Do not use any underscore(_) or hyphen(-) for multiple word project names. i.e rokomari, orderservice, quotationservice etc. This will keep the package names clean.

1. Place the Hibernate entity classes in the entity package.

1. Use repository and service packages for Repository and Service classes.

1. Place view template based controllers in the web.controller package and rest controllers in the web.restcontroller package.

1. For cloud projects (config server, eureka server, cloud services etc) and services i.e you need to add cloud dependencies in gradle.build file. Make sure you have these property blocks in your build.gradle file - 

    ```yaml
    ext {
        set('springCloudVersion', "Hoxton.SR3")
    }

    dependencyManagement {
        imports {
            mavenBom "org.springframework.cloud:spring-cloud-dependencies:${springCloudVersion}"
        }
    }
    ```


## API Design Guide

1. You should not directly map database tables into the API. So Entity/Document classes should never be exposed by an API. Use a DTO class instead.

1. Do not directly receive Entity/Document class object from request. Use a DTO class instead.

1. Do not use 'DTO' suffix for a DTO class. **more on this later** 

1. Avoid using verb in API URL. Use resource name instead.

1. Use versioning in API. For example - 

        GET     walletservice/api/v1/transactions
    
    1. We are accessing a walletservice API in this example.
    1. This in API version 1
    1. We are accessing transaction resource

1. Use HTTP verb to specify action on resources.

        1. GET     walletservice/api/v1/transactions
        2. GET     walletservice/api/v1/transactions/[transation_id]
        3. POST    walletservice/api/v1/transactions   [body with transation info]
        4. PUT     walletservice/api/v1/transactions/[transaction_id]   [body with transation info]
        5. DELETE  walletservice/api/v1/transactions/[transaction_id]

    1. Returns list of Transaction
    1. Returns a single Transaction with given transaction_id
    1. Creates a new Transaction with given transaction info in the body
    1. Updates existing transaction of given transaction_id with given transaction info in the body
    1. Deletes the transaction wtih given transaction_id

1. Add filtering values in the URL with parameter.

        GET     walletservice/api/v1/transactions?status=ACTIVE&name=asdf

1. in, gt these can be used for advanced filtering.

1. Add pagination in the URL with parameter. page_size should be optional. Use a upper boundary value for page_size in the service.

        GET     walletservice/api/v1/transactions?page_no=5&page_size=50



## Application Architecture

1. Do no Inject Repository classes directly into Controller classes. Repository layer should close to database and Service layer with all the business logic.  



## Application Properties

1. For Monolithic application always use these properties as first two. Although application.name property is not that useful in monolithic case, but we will use it for the sake of future microservice migration. Server port is not fixed, it better to mention it explicitly. 

    ```yaml
    spring.application.name=spring-boot-mysql
    server.port=8080
    ```

1. Use these properties for MySQL -

    ```yaml
    spring.datasource.url=jdbc:mysql://localhost:3306/spring-boot-mysql_db
    spring.datasource.username=root
    spring.datasource.password=root
    ```

1. Remove MySQL properties from production. Try to maintain this type of difference using profile. ddl-auto's default value is none, which does to do any database changes from hibernate entity. Production database change should be executed separately. 

    ```yml
    spring.jpa.show-sql = true
    spring.jpa.hibernate.ddl-auto = update
    ```


## Application Folder Structure

1. Use following folder structure. 

        └───springbootmysql
            ├───config                  <- all the configs, use inner package if needed
            |   ├───redis
            |   └───solr        
            ├───domain                  <- hibenate mapping classes
            ├───enumeration             <- enumerations which are used multiple class wide
            ├───exception               <- custom exceptions
            ├───model                   <- model classes used inside application or for REST APIs
            ├───repository
            ├───service
            ├───utility
            └───web
                ├───controller          <- view template based controllers
                └───restcontroller      
                    └───v1              <- 1st version rest controllers


## Banner

1. Add custom banner in the Spring Boot project.

    1. From here - http://patorjk.com/software/taag/#p=display&f=Graffiti&t=Type
    1. Use Big font

1. Add project info text under the banner. Add main project name before service name for microservice.

        :: rokomari_notificationservice :: Spring Boot${spring-boot.formatted-version} :: (c) OWSL 2012-2020 ::


## Database

1. Whatever database you choose just add ‘_db’ after the application name and use that as the database name. For the quotationservice application, the database name will be quotationservice_db. If it is a microservice add the application name in from of it. If quotationservice is a microservice and part of notebook application, use notebook_quotationservice_db as the database name.

1. Use underscore based small letter naming convention for table names and table column names. i.e customer_order, product_purchase. Avoid any sort of short name or acronym for table names.


## Datatype

1. Do not use Float or Double for monetory calculations. Use BigDecimal.


## Docker

1. Use container_name property in docker_compose.yml file. Naming format would be [application_name]_[service_name]_[container_service_name]. If redis is used for Rokomari application's quotationservice service -

    ```yml
    version: "3.5"

    services:

        redis:
            container_name: rokomari_quotationservice_redis
            image: redis
            ports:
                - "6380:6379"
            restart: on-failure
    ```


## File and Method Naming

1. View files
1. Static folders (image, css, javascript, favicon etc)
1. Controllers and methods
1. Services and methods
1. Repositories and methods


## General Convention

1. Do not use Property level Autowiring. Use Constructor level Autowiring.


## Hibernate

#### This guide is specifically for Spring Boot projects.

1. Use just the @Entity annotation on top of a Entity class. Spring Boot automatically derives table name from class name (i.e PostDoc to post_doc), so @Table annotation is not needed.

    ```java
    @Entity
    public class Tag {
        ...
    }
    ```

1. Use Enum for multi valued properties (i.e Status with value ACTIVE and INACTIVE). Place those at the bottom of the Entity class. Create an enum in enumeration package only if it is usable in more than one classes.

    ```java
    @Entity
    public class Tag {
        ...
        ...

        public enum Status {ACTIVE, INACTIVE}
    }
    ```

1. These are 5 must have properties for every Domain - id, createdBy, updatedBy, createdAt, updatedAt. Use AbstractAuditingEntity. All the fields except id is managed by the AuditingEntityListener class.

1. id, createdBy, updatedBy, createdAt, updatedAt - these are 5 must have properties for all the Entity classes. Do not define these in all classes. Use an AbstractAuditingEntity class and extend this from all the Entity classes. There could be some special cases, when primary key generation strategy is not same all over the project. But this is very unlikely.

    ```java
    import org.springframework.data.jpa.domain.support.AuditingEntityListener;
    import org.springframework.format.annotation.DateTimeFormat;

    import javax.persistence.EntityListeners;
    import javax.persistence.GeneratedValue;
    import javax.persistence.GenerationType;
    import javax.persistence.Id;
    import javax.persistence.MappedSuperclass;
    import javax.validation.constraints.NotNull;
    import java.time.Instant;

    @MappedSuperclass
    @EntityListeners(AuditingEntityListener.class)
    public abstract class AbstractAuditingEntity {

        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        private Long id;

        @NotNull
        @DateTimeFormat(pattern = "dd-MMM-yyyy")
        private Instant createdAt;

        @DateTimeFormat(pattern = "dd-MMM-yyyy")
        private Instant updatedAt;

        @NotNull
        private String createdBy;

        private String updatedBy;

        public Long getId() {
            return id;
        }

        public void setId(Long id) {
            this.id = id;
        }

        public Instant getCreatedAt() {
            return createdAt;
        }

        public void setCreatedAt(Instant createdAt) {
            this.createdAt = createdAt;
        }

        public Instant getUpdatedAt() {
            return updatedAt;
        }

        public void setUpdatedAt(Instant updatedAt) {
            this.updatedAt = updatedAt;
        }

        public String getCreatedBy() {
            return createdBy;
        }

        public void setCreatedBy(String createdBy) {
            this.createdBy = createdBy;
        }

        public String getUpdatedBy() {
            return updatedBy;
        }

        public void setUpdatedBy(String updatedBy) {
            this.updatedBy = updatedBy;
        }
    }
    ```

    ```java
    @Entity
    public class Tag extends AbstractAuditingEntity {
        ...
    }
    ```

1. Use Hibernate/JPA annotations on property level. Mixing up annotation on property and setter levels creates compilation issue.

1. Use Long data type and IDENTITY GenerationType for the id property (primary key). Do not use TABLE or SEQUENCE GenerationType. Those strategies maintains an extra table in the database. Define the id property in AbstractAuditingEntity class. This is applicable for SQL databases. Need to figure out the way for no-SQL databases.

    ```java
    @@Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    ```

1. Use @NotNull annotation to define not null validation for a property. Using this annotation will also create the column with nullable in database. So no need to use @Column(nullable = true) annotation. Use @Size annotaion to define minimum and maximum length limit. This will be used for entity validation. max value will be used as varchar length in database. Do not use @NotEmpty or @NotBlank annotations. Using those will not create not nullable column in database.

    ```java
    @NotNull
    @Size(min = 5, max = 1023)
    private String title;
    ```

1. Use following for huge texts. This will create text type column in database. Drop the @NotNull annotation if not neede.

    ```java
    @NotNull
    @Column(columnDefinition = "TEXT")
    private String content;
    ```

1. Use @Enumerated annotation for enum properties. Most of the cases @NotNull property will be needed.

    ```java
    @NotNull
    @Enumerated(EnumType.STRING)
    private Status status;
    ```

1. If nullable=false needed in database column (which makes not nullable in application), use @NotNull annotion in Entity.

1. Use 127, 255, 511, 1023, 2047, 4095 as String length. For lengthier cases use TEXT. These are few examples. 

    ```java
    @NotNull
    @Size(min = 1, max = 255)
    private String name;

    @NotNull
    @Size(min = 5, max = 255)
    private String password;

    @NotNull
    @Size(min = 5, max = 255)
    @Column(unique = true)
    private String email;

    @NotNull
    @Size(min = 5, max = 255)
    @Column(unique = true)
    private String phone;

    @DateTimeFormat(pattern = "dd-MMM-yyyy")
    private Date dateOfBirth;

    @NotNull
    @Size(min = 5, max = 1023)
    private String title;

    @NotNull
    @Size(min = 5, max = 2047)
    private String topSummary;

    @NotNull
    @Column(columnDefinition = "TEXT")
    private String content;
    ```

1. JOINs - yet to come....

1. Explicitly disable Entity class default constructor with a private access modifier. Use a static method for instance creation. Use newObjectWithDefaults as method name. Assign all the default properties in this method.

    ```java
    private Tag() {
    }

    public static Tag newObjectWithDefaults() {
        Tag tag = new Tag();
        tag.postCount = 0;
        return tag;
    }
    ```



## Port Arrangement

1. Use Config server’s (configserver) port as 8888.

1. Use Eureka server’s (eurekaserver) port as 8761.


## View Layer

1. Use hyphen separated small case for URL.

        rokomari.com/this-is-an-example-url

https://specs.openstack.org/openstack/api-wg/guidelines/pagination_filter_sort.html