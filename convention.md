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

    ```java
    var s = "JavaScript syntax highlighting";
    alert(s);
    ```