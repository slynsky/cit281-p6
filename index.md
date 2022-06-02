## Project Purpose and Components
This project was a further exploration of classes, which also asked students to work on their debugging capabilities.

## What I Learned
It was really fun to do this project, because it reminded me of puzzles (my favorite hobby). It helped me understand classes better, and I felt accomplished when I was able to test and debug my code.

## Code
### p6.js
class Shape {
    constructor(sides = []) {
        this.sides = sides;
    }
    perimeter = () => {
        return (this.sides[0] !== undefined ? this.sides.reduce((previousValue, currentValue) => previousValue + currentValue): 0);
    }
}

/*
console.log(new Shape([5, 10]).perimeter());  // 15
console.log(new Shape([1, 2, 3, 4, 5]).perimeter()); // 15
console.log(new Shape().perimeter()); // 0
*/
// Shape class works with tester code

class Rectangle extends Shape {
    constructor(length=0, width=0) {
        super([length, width, length, width]);

        this.length = length;
        this.width = width;
    }
    area = () => {
        return this.length*this.width
    }
}

/*
console.log(new Rectangle(4, 4).perimeter());  // 16
console.log(new Rectangle(4, 4).area());  // 16
console.log(new Rectangle(5, 5).perimeter()); // 20
console.log(new Rectangle(5, 5).area()); // 25
console.log(new Rectangle().perimeter()); // 0
console.log(new Rectangle().area()); // 0
*/
// Rectangle class works with tester code

class Triangle extends Shape {
    constructor (sideA=0, sideB=0, sideC=0) {
        super([sideA, sideB, sideC]);

        this.sideA = sideA;
        this.sideB = sideB;
        this.sideC = sideC;
    }
    area = () => {
        let half = this.perimeter()/2;
        //let rootExpression = ;
        return (Math.sqrt(half*(half-this.sideA)*(half-this.sideB)*(half-this.sideC)));
    }
}

/*
console.log(new Triangle(3, 4, 5).perimeter());  // 12
console.log(new Triangle(3, 4, 5).area());  // 6
console.log(new Triangle().perimeter()); // 0
console.log(new Triangle().area()); // 0
*/
// Triangle class works with tester code

// Array of sides arrays
const data = [ [3, 4], [5, 5], [3, 4, 5], [10], [] ];

for (let sidesArray of data) {
    let sides = sidesArray.length;
    let sidesString = sidesArray.toString();
    switch(sides) {
        case 2:
            let newRectangle = new Rectangle(...sidesArray)
            console.log(newRectangle.length === newRectangle.width ? `Square with sides ${sidesString} has perimeter of ${newRectangle.perimeter()} and area of ${newRectangle.area()}` : `Rectangle with sides ${sidesString} has perimeter of ${newRectangle.perimeter()} and area of ${newRectangle.area()}`);
            break;
        case 3:
            let newTriangle = new Triangle(...sidesArray)
            console.log(`Triangle with sides ${sidesString} has perimeter of ${newTriangle.perimeter()} and area of ${newTriangle.area()}`);
            break;
        default:
            console.log(sides === 1 ? `Shape with ${sides} side unsupported` : `Shape with ${sides} sides unsupported`)
    }
}

### [Home Page](https://slynsky.github.io)
