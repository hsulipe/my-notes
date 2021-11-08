# Builder Pattern

## Objective

Make a simple description of the builder pattern.  

## Description

Builder pattern separates the construction of a complex object from its representation. Builder pattern builds a complex object using simple objects by providing a step by step approach. It belongs to the creational patterns.  

## Components

- Builder Interface - Since vanilla javascript don't allow interfaces this will be removed from the example.
- Concrete Builder
- build method
- buildPart methods
- Generated object

## Examples

- Javascript
```javascript
let GameScoreBuilder = function () {

    let gameName;
    let userId;
    let score = 0;
    let creationDate = new Date();

    return {
        setGameName: function (name) {
            this.gameName = name;
            return this;
        },
        setUserId: function (userId) {
            this.userId = userId;
            return this;
        },
        setScore: function (score) {
            this.score = score;
            return this;
        },
        setCreationDate: function (creationDate) {
            this.creationDate = creationDate;
            return this;
        },
        build: function () {
            return new GameScore(gameName, userId, score, creationate);
        }
    };
};


const gameScore = new GameScoreBuilder()
    .setGameName('Valorant')
    .setUserId('1234-4321')
    .setScore(100)
    .build()
```

- C#
```C#
interface IGameScoreBuilder {
    IGameScoreBuilder setGameName();
    IGameScoreBuilder setUserId();
    IGameScoreBuilder setScore();
    IGameScoreBuilder setCreationDate();
}

class GameScoreBuilder : IGameScoreBuilder {
    private String GameName { get;set; }
    private String UserId { get;set; }
    private int Score { get;set; }
    private DateTime CreationDate { get;set; }

    GameScoreBuilder setGameName(name) {
        this.GameName = name;
        return this;   
    }

    GameScoreBuilder setUserId(userId) {
        this.UserId = userId;
        return this;   
    }

    GameScoreBuilder setScore(score) {
        this.Score = score;
        return this;   
    }

    GameScoreBuilder setCreationDate(creationDate) {
        this.CreationDate = creationDate;
        return this;   
    }

    GameScore Build () {
        return new GameScore(this.GameName, this.UserId, this.Score, this.CreationDate);
    }
}

class GameScore {
    private String GameName { get;set; }
    private String UserId { get;set; }
    private int Score { get;set; }
    private DateTime CreationDate { get;set; }

    public GameScore (name, userId, score, creationDate) {
        this.GameName = name;
        this.UserId = userId; 
        this.Score = score;
        this.CreationDate = creationDate;
    }
}

class Program {
    static void Main(string[] args)
    {
        IGameScoreBuilder builder = new GameScoreBuilder();
        GameScore score = builder.setGameName("Valorant")
            .setScore(100)
            .setUserId("1234-4321")
            .setCreationDate(DateTime.Now)
            .Build();
    }
}
```


## References
[Builder Pattern](https://zetcode.com/javascript/builderpattern/)  
Design Patterns, by The Gang of four