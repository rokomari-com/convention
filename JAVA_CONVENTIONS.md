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

