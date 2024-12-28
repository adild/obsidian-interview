- Spring is a dependency injection framework to make java application loosely coupled.
- it removes tightly coupled code so that later if we want to changes something it should not be very tightly coupled.
- It makes easy development of javaEE application.
<h4>Dependency Injection</h4>
- Its a design pattern which helps to design applications.
- Example -
```
class Ramu {
	Geeta ob;
	public void doWork() {
			
	}
}

class Geeta {
	public void doWork() {
			
	}
}
```

- In the above example, Ramu class has object Geeta which gonna use. ie it has dependency on Geeta class help to procced.
- Dependency means one class is dependent on another class for its work.
- we can eliminate this dependency using new keyword ie use Geeta ob = new Geeta(); but if we use new keyword it will become highly coupled.
- Dependency Injection will automatically creates the Geeta object and inject it into Ramu internally so that we don't have to use new keyword. This whole process is called Inversion of Control (IOC).
<h4>IOC container</h4>
- IOC container comes under spring framework as a component.
- Its some of the functions are to create objects, hold objects in memory, inject one object into another ie dependency injection.
- Basically it maintains lifecycle of an object from its creation to destroy.
- It needs 2 things to process -
	- 1) Beans - POJO Classes to manage
	- 2) Configuration - which bean depends on which bean
- Using configuration, spring container will understand how to deal with beans.
- After doing injection, application code can use the beans created by container using get.
<h4>ApplicationContext</h4>
- ApplicationContext is an interface.
- It is basically IOC Container ie represents IOC Container.
- it implements beanFactory interface. So all properties of beanFactory are inherited by ApplicationContext.
- ApplicationContext is a interface so we cant create object, so we create object of its sub class. 
- sub classes are -
	-  ClassPathXmlApplicationContext
	- AnnotationConfigApplicationContext
	-  FileSystemXmlApplicationContext
- more info - https://stackoverflow.com/questions/19615972/application-context-what-is-this
- Dependency injection done by IOC container can be done in 2 ways () -
	- more info in video - https://youtu.be/bICqNfzUG4c?list=PL0zysOflRCekeiERASkpi-crREVensZGS&t=304
	- using setter injection
	- using constructor injection
- configuration file (below video provides all info on this)- 
- https://youtu.be/bICqNfzUG4c?list=PL0zysOflRCekeiERASkpi-crREVensZGS&t=716
- practical example to use setter injection using xml - 
	- https://youtu.be/C2p1ngCq5KY?list=PL0zysOflRCekeiERASkpi-crREVensZGS&t=700
<h4> Life Cycle methods of Spring Bean </h4>
- beans are nothing but java classes. 
- theory - https://www.youtube.com/watch?v=jChQnUMsW7k&list=PL0zysOflRCekeiERASkpi-crREVensZGS&index=13
- more info in simple terms - https://medium.com/@sendvjs/spring-bean-life-cycle-9363332c335e
- it provides two methods to every bean by default. These are:

	1) public void init() 2) public void destroy()
- Execution of flow of program when application is started - 
	- When we run the program, first of all, the spring container gets started. After that, the container creates the instance of a bean as per the request, and then the required dependencies are injected. At the end, the bean is destroyed when the spring container is closed.
- practical example using xml - https://www.youtube.com/watch?v=eRKQqHTHqHI&list=PL0zysOflRCekeiERASkpi-crREVensZGS&index=14
- practical example using interfaces - https://www.youtube.com/watch?v=Xt5r19Ax4ag&list=PL0zysOflRCekeiERASkpi-crREVensZGS&index=15 
- practical example using annotation - https://www.youtube.com/watch?v=lDC15I7AH6E&list=PL0zysOflRCekeiERASkpi-crREVensZGS&index=16
<h4>Autowiring</h4>
- Feature of spring framework in which spring container inject the dependencies automatically.
- Autowiring cant be used to inject primitive and string values. It works with reference only (ie objects).
- simply autowiring will inject one object into another automatically. See the above example of Ramu and Geeta. Ramu is dependent on Geeta. We are already doing dependency injection in previous points but there we were doing it manually like using xml config to find object reference and setting the values using <ref bean = "" />. But with autowiring we can do this automatically.
- 2 ways to achieve autowiring - 
	- xml - using autowiring modes such as no, byName, byType, constructor, autodetect
	- annotations - @Autowired
- practical using xml (not important) - https://www.youtube.com/watch?v=k_ZWbZBuHqY&list=PL0zysOflRCekeiERASkpi-crREVensZGS&index=18
- practical using @Autowired annotation - https://youtu.be/jPA6tz8YNiA?list=PL0zysOflRCekeiERASkpi-crREVensZGS&t=235
- The @Autowired annotation is a core feature of Spring that automatically injects dependencies into classes, eliminating the need for manual configuration. It's part of Spring's inversion of control (IoC) container, which manages the configuration and lifecycle of application objects. 
  Here are some things to know about the @Autowired annotation:
- **How it works**
    When Spring scans code for beans, it identifies dependencies and tries to find matching beans in the application context. If it finds a single matching bean, it injects it into the target class. 
- **Where to apply**
    The @Autowired annotation can be applied to variables, methods, and constructors. 
- **How to enable**
    To use the @Autowired annotation, you need to enable annotation-based configuration in the spring bean configuration file. 
- **How to resolve ambiguities**
    If Spring finds multiple matching beans, it considers it an ambiguity. You can use the @Qualifier annotation to resolve this by providing the bean name that will be used for autowiring.
    
- @Qualifier annotation -  **helps in injecting specific beans when there are multiple candidates of the same type**.
<h4>Stereotype Annotations </h4>
- So far ie earlier in this we were using <bean / >tag in xml to create bean of an object.
- Now we using Stereotype Annotations so we can eliminate the use of <bean /> tag.
- @Component annotation is used instead of <bean /> tag to create a bean of an object so IOC container can use it.
- Example - 
```
@Component
class Student {

}
```
- In above example, IOC container scans the Student class and found that it has @Component annotation so it creates the bean/object of the class at runtime.
- So we can say <bean /> and @Component are same.
- practical - https://youtu.be/4gng9A7fXa8?list=PL0zysOflRCekeiERASkpi-crREVensZGS&t=378
- 


