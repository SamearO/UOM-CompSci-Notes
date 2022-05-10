# Java Generics

Generics allow for the passing of arbitrary types to functions and classes. 
```java
// T and U are 2 different objects that can be of arbitrary classes
public class GenericClass<T, U> {
    private T value; 

    public void setValue(T, valueIn) {
        value = valueIn;
    }

    public T getValue() {
        return value;
    }
}
```

Since the objects are of unknown classes, the only methods that can be used on them are methods that apply to `Object`. This can be too restrictive hence, bounding can be used to ensure that only classes that are subclasses of a superclass are passed as generics, hence methods of the superclass can be used. 

Below is the setup for the example

```java
// Defining the superclass
public interface SuperClass {
    public int superClassMethod();
}

public class FirstSubClass implements SuperClass {

    // Overriding the interface with a dummy method
    @Override
    public void superClassMethod() {
        return 5;
    }
}

public class SecondSubClass implements SuperClass {

    // Overriding the interface with a dummy method
    @Override
    public void superClassMethod() {
        return 6;
    }
}
```

Generic method that uses subclasses of `SuperClass`

```java 
public class UsesBoth<T extends SuperClass, U extends SuperClass> {
    // A method that's been defined in the interface, hence Java knows both classes will implement it hence it can be used.
    public int someMethod(T first, U second) {
        return T.superClassMethod() + U.superClassMethod();
    }
}
```

## Wildcards

Functions that use generics can require nesting, eg using objects that themselves allow for generics. The specificity of the function can be different than that of the input class for its generics, hence wildcards can be used.

```java 
static void someFunction(GenericClass<? extends SuperClass> objectIn){};
```

Hence this method will work for `GenericClass` if it was instantiated by SuperClass or a subclass of SuperClass.
