# Observer Pattern


## Objective

The main purpose of the Observer Pattern is to notify about any modification made on the observable objects. 


## Components

The observer pattern is composed by the following structures:

- Subject</br>
    - The main object of this pattern, is the object that can be observed by others and the one that contains the methods subscribe, unsubscribe and notify.
- Observers property</br>
    - An list of objects that will be notified when the observable object changes.
- subscribe method</br>
    - An method to add objects to the list of observers.
- unsubscribe method</br>
    - An method to remove objects from the list of observers.
- notify method
    - An method to notify all observers about the modification on the observable object.


## Example

- JavaScript
```javascript
class Subject {
    observers;
    constructor() {
        this.observers = [];
    }

    subscribe (observer) {
        this.observers.push(observer);
    }

    unsubscribe (observer) {
        this.observers = this.observers.filter(subscriber => subscriber !== observer);
    }

    notify(data) {
        this.observers.forEach(observer => observer(data));
    }
}

function main () {
    const ob = new Subject()

    const print1 = data => { console.log(`Sub_1: ${data}`) }
    const print2 = data => { console.log(`Sub_2: ${data}`) }
    const print3 = data => { console.log(`Sub_3: ${data}`) }

    ob.subscribe(print1)
    ob.subscribe(print2)
    ob.subscribe(print3)
    setTimeout(() => { ob.notify("Hello World") }, 5000 )
}
```

- C#
```c#
abstract class Subject {
    public Subject () { }
    private readonly Observer[] observers = new List<Observer>();

    public void Subscribe (Observer o) {
        observers.Add(o);
    } 

    public void Unsubscribe (Observer o) {
        observers.Remove(o);
    }

    public void Notify () {
        foreach(Observer o in observers) {
            o.Update(this);
        }
    }
}

abstract class Observer {
    
}
```

- C++
```c++
class Subject {
    public: 
        virtual ~Subject();

        virtual Subscribe(Observer*);
        virtual Unsubscribe(Observer*);
    protected:
        Subject();
    private:
        List<Observer*> *_observers;
}

void Subject::Subscribe(Observer* o) {

}
```


## References

- [Padrões em JS: Observer Pattern](https://oieduardorabelo.medium.com/padr%C3%B5es-em-js-observer-pattern-bff0ecc55d01)
- Design Patterns, by The Gang of four.