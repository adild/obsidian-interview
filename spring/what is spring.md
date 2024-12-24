- Spring is a dependency injection framework to make java application loosely coupled.
- it removes tightly coupled code so that later fi we want to changes something it should not be very tightly coupled.
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

- In the above example, Ramu class has object Geeta which gonna use. ie it has dependency on Geeta class help to procedd.
- Dependency means one class is dependent on another class for its work.
- we can eliminate this dependency using new keyword is use Geeta ob = new Geeta(); but if we use new keyword it will become highly coupled.
- Dependency Injection will automatically creates the Geeta object and inject it into Ramu internally so that we dont have to use new keyword. This whole process is called Inversion of Control (IOC).