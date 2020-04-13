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

1. JOINS - yet to come....





