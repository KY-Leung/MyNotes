## Basics

#### Optionals

> Used in situation in which a value may be absent
>
> There is a value, and it equals x OR There isn't a value at all

```swift
var myCode: Int? = 404	// either an Int or nothing
myCode = nil		   // set an optional variable to a valueless state

var myString: String?   // auto set to nil
```



## Control Flow & Collections

#### Case ... Where

```swift
let myPoint = (1, -1)
switch myPoint {
  case let (x,y) where x == y:
  	break
  case let (x,y) where x == -y:
  	break
  default:
  	break;
}
```



#### While Loop

```swift
while x > 0 {
	x--
}
```

#### Repeat-While

```swift
repeat {
	x--
} while x > 0
```



#### For-In Loop

```swift
for index in 1...5{swift
}
```



#### Control Transfer Statements

##### Continue

> Stops the loop, then restarts it at the beginning of its next cycle

##### Break (*Switch cases auto break after 1st matching case* )

> Immediately end the execution of an entire control flow statement

##### Fallthrough

>Does not check case conditions in which execution falls
>
>Fall through the next case and when that case was executed, it would break



#### Array

```swift
shoppingList.append("Flour")			// add a new item at the array's end
shoppingList += ["Juice"]				// add an array of one or more compatible items
shoppingList += ["Chocolate", "Cheese"]  

shoppingList[4...6] = ["Chocolate", "Cheese"]	// Modifying an array

shoppingList.insert("Syrup", atIndex: 0)
let syrup = shoppingList.remove(at: 0)
let apples = shoppingList.removeLast()

for item in shoppingList {
}

for (index, value) in shoppingList.enumerate() {
}
```



#### Set

> Stores distinct values. Item order is not a concern.

```swift
var names: Set = ["David", "Susan", "Robert"]

names.insert("Paul")

if names.contains("James"){
}

for name in names {
}

for name in name.sorted() {
}
```



#### Dictionaries

```swift
var airports = [Int: String]()
var airports: [String: String] = ["TOR": "Toronto", "NY": "New York"]

let oldValue = airports.updateValue("New York", forKey: "NY")
let removedValue = airports.removeValue(forKey: "NY")

for (airportCode, airportName) in airports {
}

for airpotyCode in airports.keys() {
}
for airpotyName in airports.values() {
}
```



## Functions, Closures

#### Multiple Input Parameters

```swift
func rangeLength(start: Int, end: Int) -> Int {
}

print(rangeLength(start: 2, end: 7))
```



#### Multiple Return Values

```swift
func minMax(array: [Int]) -> (min: Int, max: Int){
	return (currMin, currMax)
}

let bounds = minMax([1, 2, 3, 4, 5])
bounds.min
bounds.max
```



#### Enumerations (lowercase)

```swift
enum Compass {
  case north	// the case keyword indicates that a new line of member values is about to be defined
  case south
  case east
  case west
}

var direction = Compass.West

enum Plannet {
  case mercury = 1, venus, earth, mars, jupiter
}
```

