- Spring is a dependency injection framework to make java application loosely coupled.
- it removes tightly coupled code so that later if we want to changes something it should not be very tightly coupled.
- It makes easy development of javaEE application. [[It is basically IOC Container]]
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
- It is basically IOC Container ie represents IOC Container.
- it implements beanFactory interface.
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
- 
