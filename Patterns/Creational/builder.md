# Builder Pattern

## Objective

Make a simple description of the builder pattern.  

## Description

Builder pattern separates the construction of a complex object from its representation. Builder pattern builds a complex object using simple objects by providing a step by step approach. It belongs to the creational patterns.  

## Components

- Builder
- build method
- Generated object

## Example

```
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


## References
[Builder Pattern](https://zetcode.com/javascript/builderpattern/)