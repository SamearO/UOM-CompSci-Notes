# Advanced Object Oriented Programming

## Inheritance
* Classes can inherit from other classes to extend their functionality by adding methods and attributes to them.
* Done using the `extend` keyword.
* Methods in the parent class can be overridden in the child using `@Override`.
* To prevent methods from being overridden, use the `final` keyword.

```java
import java.lang.Math; 

public class Point3d extends Point2d {
    private int z;
    public Point3d(int x, int y, int z) {
        super(x, y); // Super calls the constructor of the parent class. Needs to be the first line
        this.z = z; // This refers to the attribute of the current object
    }

    // Creating methods that don't exist in the parent class.
    // Final so that any class extending Point3d cannot override this method.
    public final int getZ() { 
        return this.z;
    }

    // Overridding a method that exists in the parent class
    @Override
    public float getDistanceFromOrigin() {
        return Math.sqrt(Math.pow(this.z) + Math.pow(this.y) + Math.pow(this.x));
    }
}
```

## Abstract Classes
* Allows for the creation of classes that cannot be instantiated. 
* Allows for the definition and implementation of methods or attributes. 
* Must be inherited by other classes to be instantiated. 
* Can define abstract methods, hence subclasses must implement the methods.

```java
public abstract class Employee {
    private String name; // Declaring attributes

    // Declaring methods
    public Employee(Strig name) {
        this.name = name;
    }
    // Abstract methods, any child inheriting Employee must implement this method
    public abstract int getSalary();
}

public class FullTimeEmployee extends Employee {
    private int salary;

    public FullTimeEmployee(String name, int salary) {
        super(name);
        this.salary = salary;
    }

    // Implementing abstract methods
    @Override
    public int getSalary() {
        return this.salary;
    }
}
```

## Interfaces
* Are used to define methods that classes that implement the interface must implement.
* Can define variables but they must be `static` and `final`.
* Classes can implement multiple interfaces at once.

```java
public interface Edible {
    public String taste = "Yummy"; //This variable is static and final
    String howToEat(); // Any classes implementing Edible must define this method
}

// Inheriting from multiple
public class Apple implements Edible, Other {

    // Implementing the methods.
    @Override howToEat() {
        return "Just bite";
    }
}
```

## Differences between abstract and interface
* Classes can inherit from multiple interfaces but not multiple abstract classes.
* Abstract classes can implement methods, interfaces cannot.
* Abstract classes can define variables that are not `static` and `final`.
