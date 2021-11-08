# Adapter Pattern

## Objective

Make a simple description of the adapter pattern.


## Description

Convert the interface of a class into another interface clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.


## Components

- Target
    - The interface that the client uses.
- Adapter
    - Implements the interface that the client expects or knows.
- Adaptee
    - The object being adapted.
- Client
    - Calls into Adapter to request a service.


## Examples
- Javascript

```javascript
function Fruit () {
    this.isMature = (name, color, smell, size) => {
        if(color === "green") {
            if (name === "lemon") {
                throw new error("Have no idea");
            }
            return false;
        }
        return true;
    }
}

function EatableFruit () { // Adaptee
    this.isRotten = (color) => (color === "gray");
    this.isSmelly = (smell) => (smell === "bad");
    this.isRipened = (smell, size) => (size === "normal" && smell === "normal");
}

function FruitAdapter () { 
    let fruit = new EatableFruit()
    
    return {
        isMature: (name, color, smell, size) => (
            (!fruit.isRotten(color)) && 
            (!fruit.isSmelly(smell)) &&
            fruit.isRipened(smell, size);
        )
    }
}

function main () { // Client
    let fruit = new Fruit();
    let adapter = new FruitAdapter();

    const goodToEat = fruit.isMature("green apple", "green", "normal", "normal");
    console.log(`Matured: ${goodToEat}`);

    const goodToEat1 = adapter.isMature("green apple", "green", "normal", "normal");
    console.log(`Matured: ${goodToEat1}`);
}
```

- C#
```c#
class IFruit {
    bool isMature (name, color, smell, size);
}

class Fruit {
    bool isMature (name, color, smell, size) {
        if(color === "green") {
            if (name === "lemon") {
                throw new error("Have no idea");
            }
            return false;
        }
        return true;
    }   
}

class EatableFruit {
    bool isRotten (string color) => color == "gray";
    bool isSmelly (string smell) => smell == "bad";
    bool isRipened (string smell, string size) => smell == "normal" && size == "normal";
}

class FruitAdapter : IFruit {
    EatableFruit fruit;

    public FruitAdapter(EatableFruit fruit)
    {
        this.fruit = fruit;
    }

    bool isMature (name, color, smell, size) => (
        (!fruit.isRotten(color)) && 
        (!fruit.isSmelly(smell)) &&
        fruit.isRipened(smell, size);
    )
}

class Program {
    static void Main(string[] args)
    {
        IFruit fruit = new Fruit();
        EatableFruit fruitAdaptee = new EatableFruit();
        IFruit adapter = new FruitAdapter(fruitAdaptee);

        bool goodToEat = fruit.isMature("green apple", "green", "normal", "normal");
        Console.WriteLine($"Mature: {goodToEat}");

        bool goodToEat1 = adapter.isMature("green apple", "green", "normal", "normal");
        Console.WriteLine($"Mature: {goodToEat1}");
    }
}
```

## References

[Adapter Design Pattern](https://sourcemaking.com/design_patterns/adapter)  
[JavaScript Adapter](https://www.dofactory.com/javascript/design-patterns/adapter)  
Design Patterns, by The gang of four.  