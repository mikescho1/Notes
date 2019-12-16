# Spring Annotations:  

##### Container (*Service Class*):  
At its core, Spring offers a *container*, often reffered to as the *Spring Application Context*, that creates and manages application components. These components or *beans*, are wired together inside the Spring application context to make a complete application, much like bricks, moretar, timber, nails, plubming, and wiring are bound together to make a house.

##### Dependency Injection:  
The act of wiring beans toghether based on a pattern is known as *dependency injection(DI)*. Rather than have components create and maintain the lifecycle of other beans that they depend on, a dependency-injected application relies on a separate entity (*the container*) to create and maintain all compenents and inject those into the beans that need them
###### @Configuration:  
* indicates to Spring that this is a configuration class that will provide beans to the Spring application context.

###### @Beans:
* the configuration's class methods are annotated with *@Bean*, indicating that the objects they return should be added as beans in the application context (where, by default, their respective IDs will be the same as the names of the methods that define them).  

##### Automatic Configuration:  
* with *component scanning*, Spring can automatically discover components from an application's classpath and create them as beans in the Spring application context.  
* with *autowiring*, Spring automatically injects the components with the other beans that they depend on.  

More recently, with the introductio of Spring Boot, automatic configuration has gone well beyond component scanning and autowiring. The most well-known enhancement is *autoconfiguration*, where Spring Boot can make reasonable guesses of what components need to be configured and wired together, based on entries in the classpath, environmental variables, and other factors.  

#### Examining the Spring Project Structure:  
###### @SpringBootApplication:  
* clearly signifies that this is a Spring Boot application. It is a composite application that combines three other annotations:  
  * ###### @SpringBootConfiguration:  
    * designates the class as a configuration class.
  * ###### @EnableAutoConfiguration:  
    * enables Spring Boot *automatic* configuration. Tells Spring Boot to automatically configure any components that it thinks you'll need.  
  * ###### @CompositeScan:  
    * enables component scanning by letting you declare other classes with annotations like *@Component, @Controller, @Serive*, and others, to have Spring automatically discover them and register them as components in the Spring application context.  
  
  ###### The Main Method:  
  The main() method calls a static *run*() method on the *SpringApplication* class, which performs the actual bootstrapping of the application, creating the Spring application context.  
* the two parameters passed to the *run*() method are a configuration class and the command-line arguments.  

#### Creating A Controller Class:  
Controllers are the major players in Spring's MVC framework. Their primary job is to handle HTTP requests and either hand a request off to a view to render HTML (browser-displayed) or write data directly to the body of a response (RESTful).
###### @Controller:  
* This annotation serves to identify this class as a controller and to mark it as a candidate for component scanning, so that Spring will discover it and automatically create an instance of the class as a bean in the Spring application context.  
###### @RequestMapping:  
* general-purpose request handling used at the class level to specify the base path.    
###### @GetMapping:  
* handles HTTP GET requests.  
###### @PostMapping:  
* handles HTTP PUT requests.  
###### @DeleteMapping:  
* handles HTTP DELETE requests.  
###### @PatchMapping:  
* handles HTTP Patch requests  

##### Working With The JDBC Template (Repository):  
###### @Repository:  
* the repository class is annotated with *@Repository* to declare that it should be automatically discovered by Spring component scanning and instantiated as a bean in the Spring application context.  

When Spring creates the JDBC Repository bean, it injects it with *JDBC Template* via the *@Autowired* annotated construction. The constructor assigns *JDBCTemplate* to an instance variable that will be used in other methods to query and insert into the database.  

##### Creating A User-Details Service:  
Spring Security's *UserDetailsService* is a rather straightforward interface. Implementations of this interface are given a user's username and are expected to either return a *UsersDetails* object or throw a *UsernameNotFoundException* if the given username doesn't turn up any results.  
 Because your *User* class implements *UserDetails*, and because *UserRepository* provides a *findByUsername*() method, they're perfectly suitable for use in a custom *UserDetailsService* implementation.

##### Creating Your Own Configuration Properties:  
Configuration properties are nothing more than properties of beans that have been designed to accept configurations from Spring's environment abstraction.

###### @ConfigurationProperties:  
* when placed on any Spring bean, specifies that the properties of that bean can be injected from properties in the Spring environment.
* there is nothing that says *@ConfigurationProperties* must be set on a controller or any other specific kind of bean. It is often placed on beans whose sole purpose in the application is to be holders of configuration data.  
* This keeps configuration-specific details out of the controllers and other application classes.  
* It also makes it easy to share common configuration properties among several beans that may make use of that information.