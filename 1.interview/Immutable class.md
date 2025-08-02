An immutable class in Java is a class whose instances cannot be modified after they are created. Once an object of an immutable class is instantiated, its state remains constant throughout its lifetime. This means that any operation that appears to modify an immutable object actually results in the creation of a new object with the desired changes, leaving the original object untouched.

To create an immutable class in Java, follow these key principles:
- Declare the class as `final`:
    This prevents other classes from extending it and potentially altering its behavior or state through inheritance.
- Make all fields `private` and `final`:
    - `private` restricts direct access to the fields from outside the class.
    - `final` ensures that the fields are initialized once (in the constructor) and cannot be reassigned afterward.
- **Do not provide setter methods**:
    Since the object's state should not change after creation, there should be no methods to modify the values of the fields.
- **Initialize all fields in the constructor**:
    All fields must be assigned their initial values when an object of the class is created.
    
- **Handle mutable objects carefully**:
    If your class contains fields that are mutable objects (e.g., `Date`, `ArrayList`, custom mutable classes):
    - **In the constructor**: Perform a "deep copy" of these mutable objects. Instead of directly assigning the passed-in reference, create a new instance of the mutable object and copy its contents. This prevents external modifications to the original object from affecting the immutable class's internal state.
    - **In getter methods**: Return a "deep copy" of the mutable object instead of returning the direct reference. This prevents external code from obtaining a reference to the internal mutable object and modifying it.
    
Example:
```
import java.util.Date;

final class ImmutablePerson {
    private final String name;
    private final int age;
    private final Date birthDate; // Mutable field

    public ImmutablePerson(String name, int age, Date birthDate) {
        this.name = name;
        this.age = age;
        // Deep copy of mutable Date object in constructor
        this.birthDate = new Date(birthDate.getTime()); 
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public Date getBirthDate() {
        // Return a deep copy of the mutable Date object in getter
        return new Date(birthDate.getTime()); 
    }

    // No setter methods
}
```