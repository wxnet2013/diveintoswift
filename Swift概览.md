```swift
println("Hello,world")
```
### 赋值
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
### 流程控制
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
### 函数和闭包
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

```swift
func hasAnyMatches(list: Int[],condition: Int -> Bool) -> Bool{
	for item in list {
		if condition(item){
			return true
		}
	}
	return false
}
func lessThanTen(number: Int) -> Bool {
	return number < 10
}
var numbers = [20, 19, 7, 12]
hasAnyMatches(numbers, lessThanTen)

```

```swift
numbers.map({
(number: Int) -> Int in 
let result = 3 * number 
return result
})
```

```swift
numbers.map({
number in 3 * number
})
```

```swift
sort([1 ,5 ,3 ,12 ,2]) {$0 > $1}
```
### 对象和类
```swift
class Shape {
	var lessThanTen = 0
	func simpleDescription() -> String {
		return "A shape with \(numberOfSides) slides."
	}
}
```

```swift
var shape = Shape()
shape.numberOfSides = 7
var shapeDescription = shape.simpleDescription()
```

```swift
class NamedShape {
	var numberOfSides: Int = 0
	var name: String
	init(name: String) {
		self.name = name
	}
	func simpleDescription() -> String {
		return "A shape with \(numberOfSides) slides."
	}
}
```

```swift
class Square: NamedShape {
	var sideLength: Double
	init(sideLength: Double,name: String) {
		self.sideLength = sideLength
		super.init(name: name)
		numberOfSides = 4
	}
	func area() -> Double {
		return sideLength * sideLength
	}
	override func simpleDescription() -> String {
		return "A square with sides of length \(sideLength)."
	}
}
let test = Square(sideLength: 5.2, name: "my test square")
test.area()
test.simpleDescription()
```

```swift
class EquilateralTriangle: NamedShape {
	var sideLength: Double = 0.0
	init(sideLength: Double,name: String) {
		self.sideLength = sideLength
		super.init(name: name)
		numberOfSides = 3
	}
	var perimeter: Double {
		get {
			return 3 * sideLength
		}
		set {
			sideLength = newValue / 3.0
		}
	}
	override func simpleDescription() -> String {
		return "An equilateral triagle with sides of length \(sideLength)."
	}
}
let triangle = EquilateralTriangle(sideLength: 3.3, name: "a triangle")
triangle.perimete
triangle.perimeter = 9.9
triangle.sideLength
```

```swift
class TriangleAndSquare {
	var triangle: EquilateralTriangle {
		willSet {
			square.sideLength = newValue.sideLength
		}
	}
	var square: Square {
		willSet {
			triangle.sideLength = newValue.sideLength
		}
	}
	init(size: Double,name: String) {
		square = Square(sideLength: size,name: name)
		triangle = EquilateralTriangle(sideLength: size,name: name)
	}
}
var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
triangleAndSquare.square.sideLength
triangleAndSquare.triangle.sideLength
triangleAndSquare.square = Square(sideLength: 50,name: "larger square")
triangleAndSquare.triangle.sideLength
```

```swift
class Counter {
	var count: Int = 0
	func incrementBy(amount: Int,numberOfTimes times: Int) {
		count += amount * time
	}
}
var counter = Counter()
counter.incrementBy(2,numberOfTimes: 7)
```

```swift
let optionalSquare: Square? = Square(sideLength: 2.5,name: "optional square")
let sideLength = optionalSquare?.sideLength
```
### 枚举和结构
```swift
enum Rank: Int {
	case Ace = 1
	case Two, Three, Four, Five, six, seven, Eight, Nine, Ten
	case Jack, Queen, King
	func simpleDescription() -> String {
		switch self {
			case .Ace:
				return "ace"
			case .Jack:
				return "jack"
			case .Queen:
				return "queen"
			case .King:
				return "king"
			default:
				return String(self.toRaw())
		}
	}
}
let ace = Rank.Ace
let aceRawValue = ace.toRaw()
```

```swift
if let convertedRank = Rank.fromRaw(3) {
	let threeDescription = convertedRank.simpleDescription()
}
```

```swift
enum Suit {
	case Spades, Hearts, Diamonds, Clubs
	func simpleDescription() -> String {
		switch self {
			case .Spades:
				return "spades"
			case .Hearts:
				return "hearts"
			case .Diamonds:
				return "diamonds"
			case .Clubs:
				return "clubs"
		}
	}
}
let hearts = Suit.Hearts
let heartsDescription = hearts.simpleDescription()
```

```swift
struct Card {
	var rank: Rank
	var suit: Suit
	func simpleDescription() -> String {
		return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
	}
}
let threeOfSpades = Card(rank: .Three, suit: .Spades)
let threeOfSpadesDescription = threeOfSpades.simpleDescription()
```

```swift
enum ServerResponse {
	case Result(String, String)
	case Error(String)
}
let success = ServerResponse.Result("6:00 am", "8:09 pm")
let failure = ServerResponse.Error("Out of cheese.")

switch success {
	case let .Result(sunrise, sunset):
		let serverResponse = "Sunrise is at \(sunrise) and sunset is at \(sunset)."
	case let .Error(error):
		let serverResponse = "Failure... \(error)"
	
}
```
### 协议和扩展

```swift
protocol ExampleProtocol {
	var simpleDescription:String { get }
	mutating func adjust()
}
```

```swift
class SimpleClass:  ExampleProtocol {
	var simpleDescription: string = "A very simple class."
	var anotherProperty: Int = 69105
	func adjust() {
		simpleDescription += " Now 100% adjusted."
	}
}
var a = SimpleClass()
a.adjust()
let aDescription = a.simpleDescription

struct SimpleStructure:  ExampleProtocol {
	var simpleDescription: String = "A simple structure"
	mutating func adjust() {
		simpleDescription += " (adjusted)"
	}
}
var b = SimpleStructure()
b.adjust()
let bDescription = b.simpleDescription
```

```swift
extension Int: ExampleProtocol {
	var simpleDescription: String {
		return "The number \(self)"
	}
	mutating func adjust() {
		self += 42
	}
}
7.simpleDescription
```

```swift
let protocolValue: ExampleProtocol = a
protocolValue.simpleDescription
// protocolValue.anotherProperty // Uncomment to see the error
```
### 泛型
```swift
func repeat<ItemType>(item: ItemType, times: Int) -> ItemType[] {
	var result = ItemType[]()
	fot i in 0..times {
		result += item
	}
	return result
}
repeat("knock",4)
```

```swift
// Reimplement the Swift standard library's optional type 
enum OptionalValue<T> {
	case None
	case Some(T)
}
var possibleInteger: OptionalValue<T> = .None
possibleInteger = .some(100)
```

```swift
func anyCommonElements <T, U where T: Sequence, U: Sequence, 
	T.GeneratorType.Element: Equatable,
	T.GeneratorType.Element == U.GeneratorType.Element> (lhs:
	T, rhs: U) -> Bool {
		for lhsItem in lhs {
			for rhsItem in rhs {
				if lhsItem == rhsItem {
					return true
				}
			}
		}
		return false
}
anyCommonElements([1, 2, 3], [3])
```