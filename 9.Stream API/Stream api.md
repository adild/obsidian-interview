
Given a array of int 
`Integer[] numbers = {1,2,3,4,5,6};`
convert it to stream of ints
`Stream<Integer> streamOfIntegers = Arrays.stream(numbers);`
now we can able to perform stream operations on streamOfIntegers

You can pass a variable number of arguments to `Stream.of()`, and it will create a stream containing those elements in the order they are provided.
```
Stream<String> stringStream = Stream.of("apple", "banana", "cherry");
Stream<Integer> intStream = Stream.of(1, 2, 3, 4, 5);
```

how to debug stream - 
Using `peek()` for Intermediate Inspection:
- The `peek()` intermediate operation allows for performing an action on each element as it flows through the stream without altering the stream's elements.
- This is useful for logging or printing intermediate values to observe the state of the stream at various points in the pipeline.
```
List<String> names = Arrays.asList("John", "Jacob", "Edward");
names.stream()
     .filter(name -> name.startsWith("J"))
     .peek(name -> System.out.println("After filter:" +name))//Inspect after filter
     .map(String::toUpperCase)
     .peek(name -> System.out.println("After map: " +name)) // Inspect after map
     .collect(Collectors.toList());
```

Example of map and filter together - 

```
listOfStudents.stream()
	.filter(stdObj -> stdObj.getAge() > 25)
	.map(stdObj -> stdObj.getName())
	.forEach(stdName -> System.out.println(stdName));
```
Remember that above forEach works on output of map, map has a output of String.
thats why in above forEach we print stdName which is String.

forEach method - 
it accepts a consumer - consumer is a functional interface which accepts something but does not return anything.
Example - 
```
forEach(stdName -> System.out.println(stdName);
or
forEach(System.out::println);
```

- Stateful intermediate operations -
sorted() is a stateful intermediate operation.
it means that sorted method will remember the elements before passing ahead.
All stateful operations does the same thing.

Example -
```
Stream.of("zia", "mia", "lia", "abhi", "lu")  
        .filter(e->  
        {  
            System.out.println("filtering: "+e);  
            return e.length() > 2;  
        })  
        .sorted()  
        .peek(e->System.out.println("after sort: "+e))  
        .forEach(System.out::println);
```
output - 
filtering: zia
filtering: mia
filtering: lia
filtering: abhi
filtering: lu
after sort: abhi
abhi
after sort: lia
lia
after sort: mia
mia
after sort: zia
zia

Observe above output - sorted() is waiting for filter to filter out elements. After it is done filtering it will sort the elements cause sorted() is stateful.

- stateful vs stateless -
Intermediate operations are further divided into _stateless_ and _stateful_ operations. Stateless operations, such as `filter` and `map`, retain no state from previously seen element when processing a new element -- each element can be processed independently of operations on other elements. Stateful operations, such as `distinct` and `sorted`, may incorporate state from previously seen elements when processing new elements.

- iterate intermediate operation -
In the context of the Java Stream API, particularly with the `Stream.iterate()` method, the "seed" refers to the initial element or starting point of the stream.

Here's how it works:

- `Stream.iterate(T seed, UnaryOperator<T> f)` (Java 8):
    
    This version creates an infinite sequential ordered `Stream` by repeatedly applying the `UnaryOperator` `f` to the previous element, starting with the `seed`.
    
    - The first element of the stream is `seed`.
    - The second element is `f(seed)`.
  Example - Here we are overriding UnaryOperator for understanding purpose.
```
Stream.iterate(0, new UnaryOperator<Integer>() {  
    @Override  
    public Integer apply(Integer integer) {  
        System.out.println("nigas: "+integer);  
        return integer+1;  
    }  
}).limit(40).forEach(System.out::println);
```

- reverse numbers -
```
Stream.of(1,2,3,5,4,3)
	.sorted(Comparator.reverseOrder())
	.forEach(System.out::println);
```

- short-circuit intermediate stateful operation -
short-circuit means that it wont process further elements if certain condition is met.
limit() is a short-circuit intermediate stateful operation.
takeWhile() is also a short-circuit intermediate stateful operation. It is similar to filter().

but question arises that why its stateful when it is short-circuit?
cause of parallel stream.
watch this - https://youtu.be/_YiNCZGVmkk?list=PL3NrzZBjk6m-jblxwCFWxtvCeYGv05rmj&t=3361


Example -
```
Stream.of("zia", "mia", "lia","abhi","lu")
	.map(e->e.length())
	.limit(2)
	.forEach(System.out::println);
o/p: 
3
3
```
Above will only allow passing of first two elements returned from map.

- skip (stateful intermediate operation) -
skips first n number of elements.
Example - 
```
Stream.of("zia", "zia", "mia", "lia","abhi","lu")
	.skip(3)
	.forEach(System.out::println);
o/p: 
lia
abhi
lu
```

- distinct (stateful intermediate operation) -
duplicate elements are elimitnated
example -
```
Stream.of("zia", "zia", "mia", "lia","abhi","lu")
	.distinct()
	.forEach(System.out::println);
o/p: 
zia
mia
lia
abhi
lu
```
