![[Pasted image 20250608114442.png]]

![[Pasted image 20250608114755.png]]

Rules - 
![[Pasted image 20250608115310.png]]

examples for above rules -
![[Pasted image 20250608120039.png]]

![[Pasted image 20250608120119.png]]

Unary operators -

![[Pasted image 20250608120311.png]]
line 25 has error. ! operator only works with boolean.

watch this example very imp - https://youtu.be/cUpCyp3WdtA?list=PLviC8AFqAj5BEtYhyh2QUgUHjzIU_61Ib&t=413

casting - 

![[Pasted image 20250608121516.png]]
line 14 overflows cause range is -128 to 127, so when (short)1921222 is given since its greater than 127 it goes back to -128 and keeps happening in cycle.

![[Pasted image 20250608121831.png]]
compilation error cause we already know compiler will convert x\*y as short values are automatically promoted to int when applying arithemetic operators. To solve above error just cast it ie (short) (x\*y)

![[Pasted image 20250608122626.png]]
line 29 also does automatic casting as well so we dont need to explicit do cast.
line 33 is fine, theres no error in it.

watch this very imp - https://youtu.be/p652oQcFg-4?list=PLviC8AFqAj5BEtYhyh2QUgUHjzIU_61Ib&t=857

equality operator (\==) 

![[Pasted image 20250609122650.png]]

Above pic, 5 == 5.00 returns true because 5 is automatic cast to double.

Below pic doesnt compile -
![[Pasted image 20250609123648.png]]
data types are imp.

![[Pasted image 20250609124005.png]]
x and y are pointing to different objects in heap memory thats why x \==y returns false.
when z is introduce,  and is assigned as z = x, so z is also pointing to object of x in heap so z = x returns true.

- If else, switch, ternary -

Below is correct and wont throw compilation error(some will think else block is not there no it will throw error) -
```
if(condition) {

} else if () {

} else if () {

}
```

![[Pasted image 20250609131159.png]]
Above doest compile.
only true and false are consider boolean when using if. see above pic for understanding.

- ternary operator - 
![[Pasted image 20250609131433.png]]

![[Pasted image 20250609131655.png]]
in above pic, 1st statement returns true - here it is sopl thats why it is correct.
2nd one compile error - as int data type cant store String "Horse".

ternary operator is also short circuit cause if condition is true then one expression is evaluated and other one is completely ignored. in above example if y<5 is true then 21 is return and "Zebra" is ignored.
another example below - 
![[Pasted image 20250609132322.png]]

- switch case - 

syntax and rules -
![[Pasted image 20250609133029.png]]
curly braces are required.
boolean is not supported - like switch(true)  {} -  this is incorrect - compilation error - not supported.

example exam question - https://youtu.be/htSD79-zHGA?list=PLviC8AFqAj5BEtYhyh2QUgUHjzIU_61Ib&t=2024


- String concatanation -
rules -
![[Pasted image 20250617171037.png]]

![[Pasted image 20250617171114.png]]

Above pic, line 17 gives error as String value cant be store in int data type.
line 22 output is 3c (remember this)

Another example - 
![[Pasted image 20250617171451.png]]
Above pic, observe line 24, 25 for data types, one of them is String.

- Immutability -
	- meaning - cannot be changed

- String methods -
![[Pasted image 20250618165210.png]]
line 18 - searches for 'al' and returns its index.
line 19 - starts the search from index 4 (second parameter).
line 20 - starts the search from index 5 but it didnt find 'al' so it returns -1

- substring - 
![[Pasted image 20250618170123.png]]
end index is open bracket, means dont inculde 4 in above example at line 26. 
line 29 - exception cause end end index cant be smaller than begin index.
line 30 - out of bound exception.

![[Pasted image 20250618170730.png]]
Above will output as the original String s because String is immutable. If we need to do upper case then we have to reassign like s = s.toUpperCase(); or assign to different variable.

![[Pasted image 20250618171402.png]]
contains is case sensitive thats why line 54 prints false

![[Pasted image 20250619134652.png]]
line 64 - trims starting and trailing spaces

![[Pasted image 20250619135454.png]]
method chaining at line 74

StringBuilder - 
watch this very imp - https://youtu.be/vXBMAhOEy90?t=768&si=qt9f-G_DVW5R_v_E

- == operator in String

- StringBuilder -
![[Pasted image 20250623131109.png]]

understanding of above example -
![[Pasted image 20250623131136.png]]

tricky question - 
![[Pasted image 20250623133244.png]]

line 23 returns false - cause at compile time " Akash" at line 22 is created on different memory address in heap pool.

- equals method in class / used with object - 
watch ve2ry imp - https://youtu.be/4caFTKiUozI?list=PLviC8AFqAj5BEtYhyh2QUgUHjzIU_61Ib&t=1082

- Array - 
![[Pasted image 20250623135029.png]]

valid array declaration - 
![[Pasted image 20250623140933.png]]
line 17 - both ids, types are of array data type

default value for array - 
![[Pasted image 20250623141908.png]]
line 5 - default to null
line 11 - creates array of size 2 and default value is [null, null]

casting of arrays - 
![[Pasted image 20250623142601.png]]
line 31 - converting object to array - carefully use [] to convert to array.

- sorting - 
![[Pasted image 20250623143718.png]]

line 50 - starting and ending index are provided as 2nd and 3rd parameter.
line 55 - prints [10, 100, 9] - cause it sorts in lexographical order - means which character comes before which character, means 1 is smaller than 9, thats why 100 is placed before 9

- var args -
imp - https://youtu.be/_lUYpcpQboc?list=PLviC8AFqAj5BEtYhyh2QUgUHjzIU_61Ib&t=2510

- 2d array - 
declaration - 
![[Pasted image 20250623150038.png]]

understanding - 
![[Pasted image 20250623150334.png]]

above array is - int[][][] ints = new int\[3\]\[2\]

questions - https://youtu.be/_lUYpcpQboc?list=PLviC8AFqAj5BEtYhyh2QUgUHjzIU_61Ib&t=3236

