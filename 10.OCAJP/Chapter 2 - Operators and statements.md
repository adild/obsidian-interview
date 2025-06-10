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


