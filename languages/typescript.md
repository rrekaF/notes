# [typescript](https://www.w3schools.com/typescript/index.php) syntax cheatsheet

## init
```sh
npx tsc --init 
npx tsc
node file.js
```
Optionally change the output directory and compile only files in ./src by changing the tsconfig.json
```json
{  
  "include": ["src"],  
  "compilerOptions": {  
    "outDir": "./build"  
  }  
}
```
## any type
```ts
let v: any = true;  
v = "string"; // no error as it can be "any" type  
Math.round(v); // no error as it can be "any" type
```
## readonly
```ts
const names: readonly string[] = ["Dylan"];  
names.push("Jack"); // Error: Property 'push' does not exist on type 'readonly string[]'.
```
## tuples
```ts
const ourReadonlyTuple: readonly [number, boolean, string] = [5, true, 'The Real Coding God'];

// Named tuple
const ourReadonlyTuple: readonly [x: number, y: string] = [5, '6'];

// Deconstructing
const [x, y] = ourReadonlyTuple; // const / let
```
## objects with optional properties
```ts
const car: { type: string, mileage?: number } = { // no error  
  type: "Toyota"  
};  
car.mileage = 2000;
```
## index signatures
```ts
const nameAgeMap: { [index: string]: number } = {};  
nameAgeMap.Jack = 25; // no error  
nameAgeMap.Mark = "Fifty"; // Error: Type 'string' is not assignable to type 'number'.
```
## enums
enums by default start at 0 and increment by 1 
```ts
enum CardinalDirections {  
  North = 2,  
  East,  
  South,  
  West = 'West'  
}
// 2, 3, 4, West
console.log(CardinalDirections.North);
console.log(CardinalDirections.East);
console.log(CardinalDirections.South);
console.log(CardinalDirections.West);

enum StatusCodes {  
  NotFound = 404,  
  Success = 200,  
  Accepted = 202,  
  BadRequest = 400  
}  
// logs 404  
console.log(StatusCodes.NotFound);  
// logs 200  
console.log(StatusCodes.Success);
```
## type aliases
```ts
type CarYear = number  
type CarType = string  
type CarModel = string  
type Car = {  
  year: CarYear,  
  type: CarType,  
  model: CarModel  
}
```
## interfaces (struct)
```ts
interface Rectangle {  
  height: number,  
  width: number  
}  
  
interface ColoredRectangle extends Rectangle {  
  color: string  
}  
  
const coloredRectangle: ColoredRectangle = {  
  height: 20,  
  width: 10,  
  color: "red"  
};
```
## union types 
value can be more than a single type
```ts
function printStatusCode(code: string | number) {  
  console.log(`My status code is ${code}.`)  
}  
printStatusCode(404);  
printStatusCode('404');
```
## optional function parameters
```ts
// the `?` operator here marks parameter `c` as optional
function add(a: number, b: number, c?: number) {
  return a + b + (c || 0);
}
```
## rest parameters
```ts
function add(a: number, b: number, ...rest: number[]) {  
  return a + b + rest.reduce((p, c) => p + c, 0);
}
```
## [casting](https://www.w3schools.com/typescript/typescript_casting.php)(unintuitive)
```ts
let x: unknown = 'hello';  
console.log((x as string).length);
```
