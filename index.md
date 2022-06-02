## Project Purpose and Components
This project was a further exploration of classes, which also asked students to work on their debugging capabilities.

## What I Learned
It was really fun to do this project, because it reminded me of puzzles (my favorite hobby). It helped me understand classes better, and I felt accomplished when I was able to test and debug my code.

## Code
### p6.js
class Shape {<br>
    constructor(sides = []) {<br>
        this.sides = sides;<br>
    }<br>
    perimeter = () => {<br>
        return (this.sides[0] !== undefined ? this.sides.reduce((previousValue, currentValue) => previousValue + currentValue): 0);<br>
    }<br>
}<br>

/*<br>
console.log(new Shape([5, 10]).perimeter());  // 15<br>
console.log(new Shape([1, 2, 3, 4, 5]).perimeter()); // 15<br>
console.log(new Shape().perimeter()); // 0<br>
*/<br>
// Shape class works with tester code<br>

class Rectangle extends Shape {<br>
    constructor(length=0, width=0) {<br>
        super([length, width, length, width]);<br>

        this.length = length;<br>
        this.width = width;<br>
    }<br>
    area = () => {<br>
        return this.length*this.width<br>
    }<br>
}<br>

/*<br>
console.log(new Rectangle(4, 4).perimeter());  // 16<br>
console.log(new Rectangle(4, 4).area());  // 16<br>
console.log(new Rectangle(5, 5).perimeter()); // 20<br>
console.log(new Rectangle(5, 5).area()); // 25<br>
console.log(new Rectangle().perimeter()); // 0<br>
console.log(new Rectangle().area()); // 0<br>
*/<br>
// Rectangle class works with tester code<br>

class Triangle extends Shape {<br>
    constructor (sideA=0, sideB=0, sideC=0) {<br>
        super([sideA, sideB, sideC]);<br>

        this.sideA = sideA;<br>
        this.sideB = sideB;<br>
        this.sideC = sideC;<br>
    }<br>
    area = () => {<br>
        let half = this.perimeter()/2;<br>
        //let rootExpression = ;<br>
        return (Math.sqrt(half*(half-this.sideA)*(half-this.sideB)*(half-this.sideC)));<br>
    }<br>
}<br>

/*<br>
console.log(new Triangle(3, 4, 5).perimeter());  // 12<br>
console.log(new Triangle(3, 4, 5).area());  // 6<br>
console.log(new Triangle().perimeter()); // 0<br>
console.log(new Triangle().area()); // 0<br>
*/<br>
// Triangle class works with tester code<br>

// Array of sides arrays<br>
const data = [ [3, 4], [5, 5], [3, 4, 5], [10], [] ];<br>

for (let sidesArray of data) {<br>
    let sides = sidesArray.length;<br>
    let sidesString = sidesArray.toString();<br>
    switch(sides) {<br>
        case 2:<br>
            let newRectangle = new Rectangle(...sidesArray)<br>
            console.log(newRectangle.length === newRectangle.width ? `Square with sides ${sidesString} has perimeter of ${newRectangle.perimeter()} and area of ${newRectangle.area()}` : `Rectangle with sides ${sidesString} has perimeter of ${newRectangle.perimeter()} and area of ${newRectangle.area()}`);<br>
            break;<br>
        case 3:<br>
            let newTriangle = new Triangle(...sidesArray)<br>
            console.log(`Triangle with sides ${sidesString} has perimeter of ${newTriangle.perimeter()} and area of ${newTriangle.area()}`);<br>
            break;<br>
        default:<br>
            console.log(sides === 1 ? `Shape with ${sides} side unsupported` : `Shape with ${sides} sides unsupported`)<br>
    }<br>
}<br>

### [Home Page](https://slynsky.github.io)
