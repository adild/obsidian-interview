- All about main class  - 
public static void main(String args[]) {
	
}

Above if anything differs JVM wont find the main method.

public static void mains(String args[]) {
	
}

Observe carefully above code, "mains" is there. Question - can above code compiles or not?
Answer - it will compile without any errors but output wont be there as JVM will try to find "main" but we dont have "main", there is "mains".

args[] -  when we run the program, we can supply values . Multiple values can be supply like - 
dog cat bee sheep - since its array, it will have indexes so 0 - dog, 1 - cat and so on...

public static void mains(String args[]) {
	sout(args[0]);
	 // O/P will be dog
}

If we supply only one value like dog and try to access like - 
public static void mains(String args[]) {
	sout(args[0]);
	sout(args[1]);
}

above code will throw arrayIndecOutOfBound exception.

- Only one public class is allowed in one .java file.
Animal.java - 
public class Animal {
	
}

public class Dog{
	
}

Above code will cause compiler error - public type Dog must be defined in its own class.

Below code will work cause Dog call dont have public keyword- 
Animal.java - 
public class Animal {
	
}

class Dog{
	
}

conclusion - a particular class can have more than one classes but only one public class is allowed.

- packages

wild cards are * ie when we use java.util.* this * is wild card means include every class from util package (not subpackages and its classes and methods).

![[Pasted image 20250605155914.png]]

See above line 5,6,7 - those are invalid import statements. 

![[Pasted image 20250605205032.png]]

Above line number 8 will throw error if it is uncommented ie 'java.util.Date' is already defined in a single-type import.
closely observe lines 1 to 5 and also line 13.

![[Pasted image 20250605205814.png]]

Above ss, compilation error code starts from line number 1, so we can assume that imports are not there and hence it is compilation error.
But in No compilation error, code starts from line 6 so we can assume imports are there in previous lines.
They do this cause of spacing issue. Remember these points.

- Constructor - 

![[Pasted image 20250605210242.png]]

line 9 is not a constructor as it has a return type, its a regular method. 
Constructors dont have return type not even void.

- instance initializer block - 

Order of execution -
![[Pasted image 20250605211443.png]]

![[Pasted image 20250605212049.png]]
Above line 5 does not compile cause it is referring to name before it gets declared.

![[Pasted image 20250605212804.png]]
Above pic, line 14 runs first as its a field. 
Then line 15 is run as its a instance initializer block.
then constructor.

- Primitive types -

![[Pasted image 20250605215544.png]]

Above, lines 28 to 31, does not compile. cause we cant put underscore as putted in those lines.
line 26 is valid, underscore can be used like that.
lines 20 to 23 - see abrivation such as b, x, F - they use to identify binary, octal, hexa numbers - these are valid.

- Reference types - 
![[Pasted image 20250605220323.png]]

Example of reference types - String, Date etc

- variables - 

![[Pasted image 20250606101746.png]]

line 14 to 17 are valid.
line 19 is not valid as multiple data types are used ie int and String in same line

![[Pasted image 20250606102657.png]]
line 23 is invalid two times double is used.
line 25 is invalid

- Identifiers - 

![[Pasted image 20250606104612.png]]

![[Pasted image 20250606104036.png]]

lines 28 to 31 are valid identifiers.
lines 33 to 36 are invalid.
line 33 starts with 3.
line 34 has @
line 35 has *

- local variables -

![[Pasted image 20250606105307.png]]
line 74 gives error as "onlyOneBranch" is initialized only if if condition not in else condition so compiler knows it is not initialized.

![[Pasted image 20250606105843.png]]
static variables are class variables.

![[Pasted image 20250606110032.png]]
Instance and class variables are initialized default even if they are not given any value.
Any data type related to String are null as default initialization. Remember the table above.
Remember above ss is only for instance and class variables not for local variables.
local variables has to be initialized before they are used.

- Scope -

![[Pasted image 20250606110928.png]]
line 18 has error cause bitesOfCheese is out of scope as it is declared on line 15.
line 27 has error cause on line 26 scope is within that block.

rules - 
![[Pasted image 20250606111127.png]]

- Ordering -

![[Pasted image 20250606122403.png]]

Below ordering is incorrect - 
![[Pasted image 20250606122808.png]]

remember below acronium for order remember
![[Pasted image 20250606122929.png]]

![[Pasted image 20250606123654.png]] 

watch this very imp - https://youtu.be/E7B2D5Xp8dg?t=411&si=fR-QsbZYy_a03mUs

IMP Questions - https://youtu.be/CT-V9BpXeyI?t=183&si=BTPBJXtfj6nrWBS_