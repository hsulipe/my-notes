# Observer Pattern


## Objective

The main purpose of the Observer Pattern is to notify about any modification made on the observable objects. 


## Components

The observer pattern is composed by the following structures:

- **Subject**  
    - The main object of this pattern, is the object that can be observed by others and the one that contains the methods subscribe, unsubscribe and notify.  
- **Observers property**  
    - An list of objects that will be notified when the observable object changes.  
- **Subscribe method**  
    - An method to add objects to the list of observers.  
- **Unsubscribe method**  
    - An method to remove objects from the list of observers.  
- **Notify method**  
    - An method to notify all observers about the modification on the observable object.  


## Example

- JavaScript  

```js
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

    public virtual void Subscribe (Observer o) {
        observers.Add(o);
    } 

    public virtual void Unsubscribe (Observer o) {
        observers.Remove(o);
    }

    public virtual void Notify () {
        foreach(Observer o in observers) {
            o.Update(this);
        }
    }
}

abstract class Observer {
    public Observer() { }
    abstract void Update (Subject s);
}

class ConcreteSubject : Subject {
    public ConcreteSubject() { }

    public void WaitAndNotify() {
        Thread.Sleep(5000);
        this.Notify();
    }
}

class ConcreteObserver : Observer {
    private readonly string Id;
    private readonly string Text;
    public ConcreteObserver (int id, string text) {
        this.Id = id;
        this.Text = text;
    }
    public void Update (Subject s) {
        Console.WriteLine($"Observer_{this.Id}: {this.Text}")
    }
}

class Program {
    static void Main(string[] args)
    {
        Subject subject = new ConcreteSubject();

        Observer observer1 = new ConcreteObserver(1, "Hello World!");
        Observer observer2 = new ConcreteObserver(2, "Hello World!");
        Observer observer3 = new ConcreteObserver(3, "Hello World!");

        subject.subscribe(observer1);
        subject.subscribe(observer2);
        subject.subscribe(observer3);        
        
        subject.WaitAndNotify();
    }
}
```

_After implementing the C# solution I realized that the names Attach and Detach better represents the oparation than subscribe and unsubscribe. The way that is represented on the Design Pattern book._

- C++  

```cpp
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
    _observers->Append(o);
}

void Subject::Unsubscribe(Observer* o) {
    _observers->Remove(o);
}

void Subject::Notify() {
    ListIterator<Observer*> i(_observers);

    for(i.First(); !i.Done(); i.Next()) {
        i.CurrentItem()->Update(this);
    }
}

class Observer {
    public: 
        virtual ~Observer();
        virtual void Update(Subject* s) = 0;
    
    protected:
        Observer();
}

class ConcreteSubject : public Subject {
    public:
        virtual ~ConcreteSubject();
        virtual void WaitAndNotify();
    
    protected:
        ConcreteSubject();
}

void ConcreteSubject::WaitAndNotify() {
    sleep(5000);
    Notify(); 
}

class ConcreteObserver : public Observer {
    public:
        ConcreteObserver(int id);
        virtual ~ConcreteObserver();

        virtual void Update (Subject*);
    private:
        int _id;
}

void ConcreteSubject::Update () {
    std::string s = std::to_string(this._id);
    std::cout << "Observer_" << s << ": Hello World!";
} 
```


## References

- [Padrões em JS: Observer Pattern](https://oieduardorabelo.medium.com/padr%C3%B5es-em-js-observer-pattern-bff0ecc55d01)
- Design Patterns, by The Gang of four.
