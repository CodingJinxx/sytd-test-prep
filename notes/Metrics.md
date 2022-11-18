# Metrics
Metrics for Code to evaluate quality and extensibility

## Quality Metrics

### Coupling
Is the degree of interdependence between classes, i.e. software modules

Good Code should strive to be low in coupling

#### Interaction Coupling
Describes the relationship caused by message passing and invocation. I.e. how much one class relies on method invocations to other classes

###### Reducing Interaction Coupling
By utilising the Liskov Substitution principle we can decouple the concrete implementation from the definition of a class. This can be done by describing a classes methods in an interface. A Class then in turn implements said interface. Using Dependency Injection the concrete implementation can be injected into the class refering to the interface at runtime.

#### Inheritance Coupling
Describes how much a class depends on its parent class

As soon as the child class begins to override most of the parents methods it can be described as tightly coupled.

##### Reducing Inheritance Coupling
Object Composition can reduce Inheritance Complexity

This is a fundamentally alternative approach to a problem by extracting certain behaviours of class into seperate classes which are then passed. Behaviours are described by interfaces, allowing the programmer to compose its classes behaviour via any concrete implementation


```cs
public interface IQuackable {
    String quack();
}

public interface IFlyable {
    String fly();
}

public class DefaultQuackBehaviour implements IQuackable {
    public String quack(){
        return "quack";
    }
}

public class LoudQuackBehaviour implements IQuackable {
    public String quack() {
        return "loudly: quack";
    }
}

public class ProudQuackBehaviour implements IQuackable{
    public String quack() {
        return "proudly and loudly: quack";
    }
}


public SqueezeQuackBehaviour implements IQuackable {
    public String quack() {
        return "squeeze";
    }
}

public class DefaultFlyingBehaviour implements IFlyable {
    public String fly() {
        return "flying high in the sky";
    }
}

public class NoFlyBehaviour implements IFlyable{
    public String fly(){
        return "can’t fly";
    }
}

@NoArgsConstructor
@AllArgsConstructor
@Data
public class Duck implements Serializable {
    private IQuackable quackBehaviour;

    private IFlyable flyBehaviour;
}

public class DuckSimulator{
    public static final void main(String args[]) {
        Duck redheadDuck = new Duck(
            new LoudQuackBehaviour(),
            new DefaultFlyingBehaviour()
        );

        Duck EntlingDuck = new Duck(
            new ProudQuackBehaviour(),
            new DefaultFlyingBehaviour()
        );

        Duck rubberDuck = new Duck(
            new SqueezeQuackBehaviour(),
            new NoFlyBehaviour()
        );
    }
}
```


### Cohesion
If an element of the software does too many things at once, it wont do it well. However the same can be said for elements that do too little, i.e. you can think of it as maybe i could have put this into something existing
When that happens it is referred to as low cohesion

Generally one should strive to build cohesive code

#### Service Cohesion
Methods of a class should not implement too much, nor too little functionality

#### Class Cohesion
A Class should not define unused attributes or methods


