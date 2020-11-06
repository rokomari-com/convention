## Package naming
- should be noun
- should be all `lowercase`
- should be only one word after each dot
- only use English words, avoid especial characters (`_` /`$` etc)
```
com.rokomari.model
```

## Class naming
- should be noun
- should be `UpperCammelCase`
- should bound the namming upto 2 words
- should not start/end with `_` / `$`
- for domain classes, use `UPERCASE` domain part postfix. (Ex: `RefundDTO` instead of ~~RefundDto~~)
- if any ***Design Pattern*** used, should add the patterns name in the postfix. (Ex: `CustomerObserver`, `ItemObservable`, `CakeFactory`)
- avoid uncommon abbreviations in naming. (Ex: use `AbstractCake` instead of ~~AbsCake~~)
```
CompanyService
```

## Interface naming
- should be `UpperCammelCase`
- should be Adjective, Ex: `Eatable`
- can be noun if the interface marked as parent class (Ex: `LocationService`) or presented as a family of classes (Ex: `List`, `Map`)
- should not start/end with `_` / `$`
```
public interface Focusable {
    ...
}
```

## Method naming
- should be verb, like giving a command/action
- should be `lowerCammelCase`
- should contains upto highest 3 params. If required > 3 params, params should wrap around into a model and pass.
- if the language support named params, priotize them.
- should be bound upto 3 words
- should not start/end with `_` / `$` (exception for `_` if language required `_` for private modification)
- avoid writting `Boolean` veriable's `getter/setter` using `is`. use `getValue()/setValue()`. (Ex: `void setCompleted(Boolean boolean)`, `Boolean getCompleted()`)
```
List<User> getAllUsers(Integer id) {
    ...
}
```

## Veriable naming
- should be noun
- should be in `lowerCammelCase`
- should bound upto 2 words
- should not start/end with `_` / `$` (exception for `_` if language required `_` for private modification)
- avoid using `is` prefix for `Boolean` data type. (Ex: use `completed` instead of ~~isComplete~~ / ~~isCompleted~~ )
```
firstName
```

## Constants naming
- should be `UPPERCASE` with `UNDER_SCORE` between words
- should be noun
- should bound upto 2 words
- should not start/end with `_` / `$`
```
MAX_PRICE
```

## Abstract Class naming
- same as `class` naming convention, but has `Base` / `Abstract` prefix
```
BaseActivity()
```

## Exception Class naming
- same as `class` naming convention, but has `Exception` postfix
```
MessageNotFoundException
```

## Enum member naming
- should be noun
- should be `UPPERCASE` with `UNDER_SCORE` between words
- upto 2 words
``` 
public enum Status {
    NOT_COMPLETE,
    COMPLETE
}
```

## Generic Type naming
- `T` for general purpose use
- `E` for collection elements
- `K` & `V` for key-value pair
```
public interface StudentMap<K,V> {
    ....
}
```

## Annotaions naming
- should be `UpperCammelCase`
- can be noun/adjective/verb based on use-case
```
public @interface EnableCaching

public @interface Depricated
```

## Unit Test Class naming
- should follow `class-under-test`'s package structure for the test class
- name should be same as `class-under-test`'s name with `Test` postfix
```
TransactionTest
```

### Integration Test Class naming
- should follow `class-under-test`'s package structure for the test class
- name should be same as `class-under-test`'s name with `IntegTest` postfix
```
TransactionIntegTest
```

### Test method naming
- method name breaks down into `4` sections. (`method-under-test`, `GIVEN block`[Optinal], `WHEN block`, `THEN block`). each block should follow `lowerCammelCase` & between them should have `under_score`.
- `GIVEN`,`WHEN`,`THEN` blocks should prefix with respective type names.
- `GIVEN` block describe the precondition of the test.
- `WHEN` block describe the condition of the test.
- `THEN` block describe the desired output of the test.
```
@Test
void getAllUsers_givenDBAccessFailure_whenDBReturnEmpty_thenShouldReturnEmptyList() {
    ...
}
```