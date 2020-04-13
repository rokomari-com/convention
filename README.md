## Hibernate

#### This guide is specifically for Spring Boot projects.

1. Use just @Entity annotation on top of a Model class. Spring Boot automatically derives table name from class name (PostDoc to post_doc), so no need to use the @Table annotation.

    ```java
    var s = "JavaScript syntax highlighting";
    alert(s);
    ```

1. Use Enum for multi valued properties (i.e Status with value ACTIVE and INACTIVE). Place the Enum at the bottom of the Domain class. 

1. These are 5 must have properties for every Domain - id, createdBy, updatedBy, createdAt, updatedAt. Use AbstractAuditingEntity. All the fields except id is managed by the AuditingEntityListener class. 

1. Use Hibernate/Jpa annotations on property level.

    ```java
    var s = "JavaScript syntax highlighting";
    alert(s);
    ```