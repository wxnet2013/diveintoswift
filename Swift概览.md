```swift
println("Hello,world")
```

```swift
var myVariable = 42
myVariable = 50
let myConstant = 42

```

```swift
let implicitInteger = 70
let implicitDouble = 70.0
let explicitDouble:Double = 70
```

```swift
let label = "The width is"
let width = 94
let widthLabel = label + String(width)

```

```swift
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."
```

```swift
var shoppingList = ["catfish","water","tulips","blue paint"]
shoppingList[1] = "bottle of water"
var occupations = [
	"Malcolm": "Captain",
	"Kaylee": "Mechanic"
]
occupations["Jayne"] = "Public Relations"

```

```swift
let emptyArray = String()[]
let emptyDictionary = Dictionary<String,Float>()
```

```swift
shoppingList = [] //Went shopping and bought everything
```

```swift
let individualScores = [75,43,103,87,12]
var teamScore = 0
for score in individualScores {
	if score > 50 {
		teamScore += 3
	} else {
		teamScore += 1
	}
}
teamScore

```

```swift
var optionalString: String? = "Hello"
optionalString == nil

var optionalName: String? = "John Appleseed"
var greeting = "Hello!"
if let name = optionalName {
	greeting = "Hello, \(name)"
}

```

```swift
let vegetable = "red pepper"
switch vegetable {
case "celery":
	let vegetableComment = "Add some raisins and make ants on a log."
case "cucumber", "watercress"
	let vegetableComment = "That would make a good tea sandwich."
case let x where x.x.hasSuffix("pepper")
	let vegetableComment = "Is it a spicy \(x)?"
default:
	let vegetableComment = "Everything tastes good in soup."
}

```

```swift
let interestingNumbers = [
	"Prime": [2,3,5,7,11,13],
	"Fibonacci": [1,1,2,3,5,8],
	"Square": [1,4,9,16,25]
]
var largest = 0
for (kind,numbers) in interestingNumbers {
	for number in numbers {
		if number > largest {
			largest = number
		}
	}
}
largest

```

```swift
var n = 2
while n < 100 {
	n = n * 2
}
n

var m = 2
do {
	m = m*2
} while m < 100
m

```

```swift
var firstForLoop = 0
for i in 0..3 {
	firstForLoop += i
}
firstForLoop

var secondForLoop = 0
for var i = 0; i < 3; ++i{
	secondForLoop += 1
}
secondForLoop

```

```swift
func greet(name:String,day:String) -> String {
	return "Hello \(name),today is \(day)."
}
greet("Bob","Tuesday")

```

```swift
func getGasPrices() -> (Double,Double,Double) {
	return (3.59, 3.69, 3.79)
}
getGasPrices()

```

```swift
func sumOf(numbers: Int...) -> Int {
	var sum = 0
	for number in numbers {
		sum += number
	}
	return sum
}
sumOf()
sumOf(42,597,12)

```

```swift
func returnFifteen() -> Int {
	var y = 10
	func add(){
		y += 5
	}
	add()
	return y
}
returnFifteen()

```

```swift
func makeIncrementer() -> (Int -> Int) {
	func addOne(number: Int) -> Int {
		return 1 + number
	}
	return addOne
}
var increment = makeIncrementer()
increment(7)
```