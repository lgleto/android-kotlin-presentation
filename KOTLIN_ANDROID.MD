---
marp: true
title: Android Kotlin Development
paginate: true
theme: graph_paper
class: lead
---
### Desenvolvimento de Jogos para Plataformas Móveis
### Programação de Dispositivos Móveis
Lourenço Gomes
lgomes@ipca.pt
tel:933823779

---

## Material
- Comutador Windows/Mac/Linux
- Android Studio
- Git
- Slack

---

# Avaliação
### Avaliação continua
- Aquisição de competências verificadas em contexto de aula, atravès de desenvolvimento pequenos projectos, até término das aulas em dezembro. 

### Trabalho de grupo
- Especificação - meados de novembro
- Defesa - Na ultima aula de janeiro
---

# Avaliação

### Exame
- Exame teórico sem consulta e sem recurso a computador
- Defesa do trabalho de grupo ou outro trabalho a combinar
(caso não seja possivel defender o trabalho de grupo)
### Nota Final
- Avaliação continua: NF = AC*50% + TG*50%
- Exame: NF = EXAME*50% + TG*50%


---
# Aquisição de competencias

```
Composable |  Funcional  | Lists | Navigation | REST  | Android  | Gameloop	| Firebase |    Clean 
     UI    | Programming |       |            |  API  |  Room    |       	|          | Architecture

     ✅           ✅          ✅        ✅         ✅       ✅          ✅         ✅           ✅  
```

---

# Conteúdo
- Linguagem de programação Kotlin, conceitos fundamentais e comparação com outras linguagens de programação.
- Conceitos fundamentais sobre dispositivos de computação móvel SDKs e Frameworks;
- Desenvolvimento de Aplicações Móveis
- Compreender o LifeCycle das aplicações e componente do Android
- Desenvolvimento de motor de jogo(EDJD)

---

## Conteúdo
- Comunicação Web seguindo a arquitecta de API REST.(LESI)
- Armazenamento de informação estruturada e não estruturada.
- Compreender o padrão de arquitetura de software Model-view-view-Model(MVVM);
- Compreender Threads e sincronização.
- Notificações push.
- Desenvolvimento de interfaces em Android Compose
- Conceitos de Programação orientada a objectos e programação funcional

---

# Kotlin

---

# Hello World
```kotlin
fun main(args: Array<String>) {
    println("Olá Mundo!")
}
```

```kotlin
fun main(args: Array<String>) {
    println("Olá Mundo!")
    println(42)
}
```
---

# Variable declarion
```kotlin
var result : Int
//Declaração explicita
var result = 0
//Declaração implicita
val a: Int = 1  // immediate assignment
val b = 2       // `Int` type is inferred
val c: Int      // Type required when no initializer is provided
c = 3           // deferred assignment
```
---

# VAR or VAL
var  - declaração de variável
val  - declaração de uma constante

---

# Null types
```kotlin
var a : Int? = null
a = 5
println(a)
// 5
a = null
var b = 6
b = null 
// compilation error
```
---

# Null safety
```kotlin
val b: String? = "Kotlin"

if (b != null && b.length > 0) {
    print("String of length ${b.length}")
} else {
    print("Empty string")
}

val a = "Kotlin"
val b: String? = null
println(b?.length)
println(a?.length) 
// Unnecessary safe call
```
---
# Null safety
```kotlin
var a : Int? = null
a = 5
a?.let { num ->
    println(num + 5)
    // 10
}

print( a!! + 5)
//10
var a : Int? = null
a = 5
…

a = null
print( a!! + 5)
// Will be raised an exception
```

---
# Elvis operator

When you have a nullable reference b, you can say "if b is not null, use it, otherwise use some non-null value”:

```kotlin
val l: Int = if (b != null) b.length else -1
```

Along with the complete if -expression, this can be expressed with the Elvis operator, written ?:

```kotlin
val l = b?.length ?: -1
```

---
# The !! operator

The third option is for NPE-lovers: the not-null assertion operator (!!) converts any value to a non-null type and throws an exception if the value is null. You can write b!!, and this will return a non-null value of b (for example, a String in our example) or throw an NPE if b is null:

```kotlin
val l = b!!.length
```

Thus, if you want an NPE, you can have it, but you have to ask for it explicitly, and it does not appear out of the blue.

---
# Safe casts

Regular casts may result into a ClassCastException if the object is not of the target type. Another option is to use safe casts that return null if the attempt was not successful:

```kotlin
val aInt: Int? = a as? Int
```

---
# Operadores
---
# Assignment Operator
```kotlin
val l = 1L + 3 // Long + Int => Long
val b = 10
var a = 5
a = b
// a is now equal to 10

if (a = b) {
// This is not valid, because x = y does not return a value.
}

a += 1
a -= 1
a *= 10
a /= 10

a ^= 2
```
---
# Arithmetic Operators
```kotlin
1 + 2       // equals 3
5 - 3       // equals 2
2 * 3       // equals 6
10.0 / 2.5  // equals 4.0

"hello, " + "world"  // equals "hello, world"
```

---
# Remainder Operator
```kotlin
9 % 4    // equals 1

//9 = (4 x 2) + 1

-9 % 4   // equals -1

//-9 = (4 x -2) + -1
```

---

# Unary Operator
```kotlin
val three = 3
val minusThree = -three       // minusThree equals -3
val plusThree = -minusThree   // plusThree equals 3, or "minus minus three"

val minusSix = -6

val alsoMinusSix = +minusSix  // alsoMinusSix equals -6

//Compound Assignment Operators
var a = 1
a += 2
// a is now equal to 3
```

---

# Comparison Operators

```kotlin
1 == 1   // true because 1 is equal to 1
2 != 1   // true because 2 is not equal to 1
2 > 1    // true because 2 is greater than 1
1 < 2    // true because 1 is less than 2
1 >= 1   // true because 1 is greater than or equal to 1
2 <= 1   // false because 2 is not less than or equal to 1

val name = "world"
if (name == "world") {
    print("hello, world")
} else {
    print("I'm sorry ${name}, but I don't recognize you")
}
```

---

# Ternary Conditional Operator
```kotlin
if (question) {
    answer1
} else {
    answer2
}

val contentHeight = 40
val hasHeader = true
val rowHeight = contentHeight + (if (hasHeader)  50 else 20)
// rowHeight is equal to 90
```

---

# Range Operators
```kotlin
for (index in 1 .. 5) {
    print("$index times 5 is ${index * 5}")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25
```
Range instantiation and range checks:
```kotlin
a..b, x in a..b, x !in a..b
```

---

# Combining Logical Operators
```kotlin
if ((enteredDoorCode && passedRetinaScan) || hasDoorKey || knowsOverridePassword){
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
```

---
# Control Flow
---

# For-In Loops
```kotlin
for (index in 1..5) {
    println("${index} times 5 is ${index * 5}")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25

val base = 3
val power = 10
var answer = 1
for (i in 1..power) {
    answer *= base
}
println("${base} to the power of ${power} is ${answer}")
```
---
# For-In Loops
```kotlin
var names = arrayListOf<String>("Anna", "Alex", "Brian", "Jack")
for (name in names) {
    println("Hello, ${name}!")
}

// Hello, Anna!
// Hello, Alex!
// Hello, Brian!
// Hello, Jack!
```
---
# While Loops
```kotlin
while (condition) {
    statements
}
```
---
# While Loops
```kotlin
val finalSquare = 25
var board = intArrayOf(finalSquare +1)

var square = 0
var diceRoll = 0
while (square < finalSquare) {
    // roll the dice
    diceRoll += 1
    if (diceRoll == 7){ diceRoll = 1 }
    // move by the rolled amount
    square += diceRoll
    if (square < board.count) {
        // if we're still on the board, move up or down for a snake or a ladder
        square += board[square]
    }
}
println("Game over!")
```
---
# do-while
```kotlin
do {
    statements
} while (condition)
```
---
# when (switch)
```kotlin
when (some_value_to_consider) {
    value 1 -> respond to value 1
    value 2,
    value 3 -> respond to value 2 or 3
    else -> otherwise, do something else
}

val someCharacter: Char = 'z'
when (someCharacter) {
    'a' -> println("The first letter of the alphabet")
    'z' -> println("The last letter of the alphabet")
    else -> print("Some other character")
}
```
---
# When
```kotlin
val someCharacter: Char = 'a'
when (someCharacter) {
    'a',
    'A' -> println("letter of the alphabet")
    else -> println("not a letter")
}

when (x) {
    0, 1 -> print("x == 0 or x == 1")
    else -> print("otherwise")
}
```

---

# when
```kotlin
when (x) {
    in 1..10 -> print("x is in the range")
    in validNumbers -> print("x is valid")
    !in 10..20 -> print("x is outside the range")
    else -> print("none of the above")
}
```
---

# when
```kotlin
fun hasPrefix(x: Any) = when(x) {
    is String -> x.startsWith("prefix")
    else -> false
}

when {
    x.isOdd() -> print("x is odd")
    x.isEven() -> print("y is even")
    else -> print("x+y is odd")
}
```

---

# continue
```kotlin
var puzzleInput = "great minds think alike"
var puzzleOutput = ""
val charactersToRemove = arrayListOf<Char>('a', 'e', 'i', 'o', 'u', ' ')
for (character in puzzleInput.toCharArray()) {
    if (charactersToRemove.contains(character)) {
        continue
    } else {
        puzzleOutput += character
    }
}
println(puzzleOutput)

// Prints "grtmndsthnklk"
```
---

# break
```kotlin
var puzzleInput = "great minds think alike"
var puzzleOutput = ""
val charactersToRemove = arrayListOf<Char>('a', 'e', 'i', 'o', 'u', ' ')
for (character in puzzleInput.toCharArray()) {
    if (charactersToRemove.contains(character)) {
        break
    } else {
        puzzleOutput += character
    }
}
println(puzzleOutput)

// Prints "gr"
```

---
# Collection Types
Arrays, Sets, Maps

---

# Arrays
```kotlin
var someInts = arrayListOf<Int>()
println("someInts is of type [Int] with ${someInts.size} items.")
// Prints "someInts is of type [Int] with 0 items.

someInts.add(3)
// someInts now contains 1 value of type Int
// someInts = arrayListOf<Int>()
// someInts is now an empty array, but is still of type [Int]

var threeDoubles = DoubleArray(3)
// threeDoubles is of type [Double], and equals [0.0, 0.0, 0.0]

var anotherThreeDoubles = DoubleArray(3) { 2.5 }
// anotherThreeDoubles is of type [Double], and equals [2.5, 2.5, 2.5]

var sixDoubles = threeDoubles + anotherThreeDoubles
// sixDoubles is inferred as [Double], and equals [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]

for ( element in sixDoubles) {
    println(element)
}
```

---

# Arrays
```kotlin
var shoppingList  = arrayListOf<String>("Eggs", "Milk")
// shoppingList has been initialized with two initial items

print("The shopping list contains ${shoppingList.size} items.")
// Prints "The shopping list contains 2 items."

if (shoppingList.isEmpty()) {
    print("The shopping list is empty.")
} else {
    print("The shopping list is not empty.")
}
// Prints "The shopping list is not empty."

shoppingList.add("Flour")
// shoppingList now contains 3 items, and someone is making pancakes
```

---

# Arrays
```kotlin
var shoppingList  = arrayListOf<String>("Eggs", "Milk")
// shoppingList has been initialized with two initial items

println("The shopping list contains ${shoppingList.size} items.")
// Prints "The shopping list contains 2 items."

if (shoppingList.isEmpty()) {
    println("The shopping list is empty.")
} else {
    println("The shopping list is not empty.")
}
// Prints "The shopping list is not empty."

shoppingList.add("Flour")
// shoppingList now contains 3 items, and someone is making pancakes

shoppingList[0] = "Six eggs"
// the first item in the list is now equal to "Six eggs" rather than "Eggs"

shoppingList.add(0, "Maple Syrup")
shoppingList.add(0, "Honey")

shoppingList[1] = "Apples"
// shoppingList now contains 7 items
// "Maple Syrup" is now the first item in the list

for ( product in shoppingList) {
    println(product)
}
```

---

# Sets
```kotlin
var shoppingList  = setOf<String>("Eggs", "Milk")
// shoppingList has been initialized with two initial items

println("The shopping list contains ${shoppingList.size} items.")
// Prints "The shopping list contains 2 items."

if (shoppingList.isEmpty()) {
    println("The shopping list is empty.")
} else {
    println("The shopping list is not empty.")
}
// Prints "The shopping list is not empty."

shoppingList = shoppingList.plus("Flour")
// shoppingList now contains 3 items, and someone is making pancakes

shoppingList = shoppingList.plus("Apples")
shoppingList = shoppingList.plus( "Maple Syrup")
shoppingList = shoppingList.plus( "Honey")

shoppingList = shoppingList.plus("Apples")
// shoppingList now contains 7 items
// "Maple Syrup" is now the first item in the list

for ( product in shoppingList) {
    println(product)
}
```

---

# Set Operations
```kotlin
val oddDigits  = setOf(1, 3, 5, 7, 9)
val evenDigits  = setOf(0, 2, 4, 6, 8)
val singleDigitPrimeNumbers = setOf(2, 3, 5, 7)

var result = oddDigits.union(evenDigits).sorted()
// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
for (n in result) print("$n ,")

result = oddDigits.intersect(singleDigitPrimeNumbers).sorted()
// []
println("intersect")
for (n in result) print("$n ,")
```

---

# Maps
```kotlin
val numbersMap = mapOf("one" to 1, "two" to 2, "three" to 3)
println(numbersMap.get("one"))
println(numbersMap["one"])
println(numbersMap.getOrDefault("four", 10))
println(numbersMap["five"])       // null
//numbersMap.getValue("six")      // exception!

val translationMapPT = mapOf(
    "hello" to "olá", 
    "Good Morning" to "Bom dia", 
    "Good bye" to "Adeus")
val translationMapES = mapOf(
    "hello" to "ola", 
    "Good Morning" to "Buenos Dias", 
    "Good bye" to "Asta lá vista")

println(translationMapPT["Good bye"])
println(translationMapES["Good bye"])
```

---

# Maps
```kotlin
val numbersMap = mapOf(
    "one" to 1, 
    "two" to 2, 
    "three" to 3)
println(numbersMap.keys)
println(numbersMap.values)
```

---

# Maps
```kotlin
val numbersMap = mapOf("one" to 1, "two" to 2, "three" to 3)
println(numbersMap + Pair("four", 4))
println(numbersMap + Pair("one", 10))
println(numbersMap + mapOf("five" to 5, "one" to 11))

val numbersMap = mapOf("one" to 1, "two" to 2, "three" to 3)
println(numbersMap - "one")
println(numbersMap - listOf("two", "four"))
```

---

# Maps
```kotlin
val numbersMap = mutableMapOf("one" to 1, "two" to 2)
numbersMap.put("three", 3)
println(numbersMap)
```

---
# Functions

---

# Functions
```kotlin
fun greet(person: String) : String {
val greeting = "Hello, " + person + "!"
    return greeting
}

println(greet( "Anna"))
// Prints "Hello, Anna!"
println(greet( "Brian"))
// Prints "Hello, Brian!"
```

---

# Function
Argument, Labels, and Parameter Names
```kotlin
fun someFunction(firstParameterName: Int, secondParameterName: Int) {
    // In the function body, firstParameterName and secondParameterName
    // refer to the argument values for the first and second parameters.
}
someFunction( 1,  2)
```

---

# Functions
Default Parameter Values
```kotlin
println(greet( ))
// Prints "Hello, John!"
println(greet( "Brian"))
// Prints "Hello, Brian!"

fun greet(person : String = "John") : String {
    val greeting = "Hello, " + person + "!"
    return greeting
}
```

---

# Function

```kotlin
var greet : (String)->String { person ->
    val greeting = "Hello, " + person + "!"
    return greeting
}

fun greet(person : String = "John") : String {
    val greeting = "Hello, " + person + "!"
    return greeting
}
```

---

# Functions multiple parts
```kotlin
fun main(args: Array<String>) {
    greetAllv2(arrayListOf<String>("António", "Joaquim"))
    greetAll("Ana", "Joana")
}

fun greetAll(vararg strings: String) {
    for ( string in strings){
        println("Hello $string!")
    }
}

fun greetAllv2( strings: ArrayList<String>) {
    for ( string in strings){
        println("Hello $string!")
    }
}
```

---
# Enumerations
```kotlin
enum class Direction {
    NORTH, SOUTH, WEST, EAST
}
```

```kotlin
enum class Color(val rgb: Int) {
    RED(0xFF0000),
    GREEN(0x00FF00),
    BLUE(0x0000FF)
}
```

---
# Enumerations

```kotlin
fun main(args: Array<String>) {

    val dir :Direction = Direction.NORTH

    when(dir) {
        Direction.NORTH -> {
            print("Where are we!")
        }
        Direction.SOUTH -> {
            print("Mauritania!")
        }
        Direction.WEST -> {
            print("Spanish!")
        }
        Direction.EAST -> {
            print("Sea!")
        }
    }
}
```
---
# Classes and Data Classes

---

# Classes
```kotlin
class SomeClass {
// class definition goes here
}
```

---
# Object Oriented Programming

#### Car 🚗
- Propriedades
    - Velocity
    - Number of wheels
    - Color
    - Cabin Temperature

- Funcionalidades ou Métodos
    - Accelerate
    - Brake
    - Turn On

---

# Object Oriented Programming
```kotlin
class Car {

    // propreties
    var velocity : Float = 0f
    var wheelsNumber : Int = 0
    var color : Color = Color.BLUE
    var cabinTemperature : Float = 0f
    var isMotorRunning : Boolean = false

    constructor ( wheels : Int, color : Color )  {
        wheelsNumber = wheels
        this.color = color
    }

    // functionality or metods
    fun accelerate  () { velocity += 5 }
    fun brake       () { velocity -= 10 }
    fun turnOn      () { isMotorRunning = true }
    fun turnOff     () { isMotorRunning = false }
}

```
---

# Class/object
```kotlin
var myCar : Car = Car(4, Color.RED)
var mySecondCar : Car = Car(4,  Color.GREEN)

myCar.accelerate()
myCar.accelerate()
println("My car is running at ${myCar.velocity} Km/h")

mySecondCar.accelerate()
println("My second car is running at ${mySecondCar.velocity} Km/h")
```

---

# inheritance
```kotlin
            Vehicle
               |
Car --- Plane --- Boat --- Moto
 🚗       🛩        |        🏍
                _________
               |         |
            Rowing      Motor
            Boat        Boat
             🚣           🚤
```
---

# inheritance
```kotlin
class Boat : Vehicle {

    constructor(model: String) : super(model)

    override fun accelerate() {
        velocity += 2
    }

    override fun brake() {
        velocity -= 1
    }

    override fun showState() {
        println("The Boat $model is running at $velocity Miles/h")
    }
}
```

---
# inheritance
```kotlin

abstract class Vehicle {

    // properties
    var velocity : Float = 0f
    var model : String = ""

    constructor(model:String){
        this.model = model
        println("New vehicle was created with name $model")
    }

    // functionality or methods
    abstract fun accelerate ()
    abstract fun brake ()

    open fun showState(){
        println("The $model is running at $velocity Km/h")
    }
}
```

---
# inheritance
```kotlin

class Car : Vehicle {

    // properties
    var wheelsNumber : Int = 0
    var cabinTemperature : Float = 0f

    constructor ( wheels : Int, model : String ) : super(model) {
        wheelsNumber = wheels
    }

    // functionality or methods
    override fun accelerate () {
        velocity += 5
    }

    override fun brake() {
        velocity -= 10
    }

}
```

---
# Access modifiers

***private*** means visible inside this class only (including all its members).
***protected*** is the same as private but is also visible in subclasses.
***internal*** means that any client inside this module who sees the declaring class sees its internal members.
***public*** means that any client who sees the declaring class sees its public members.

---

# Access modifiers
```kotlin
abstract class Vehicle {

    // properties
    protected var velocity : Float = 0f
    private var model : String = ""

    constructor(model:String){
        this.model = model
        hello()
    }

    // functionality or methods
    abstract fun accelerate ()
    abstract fun brake ()

    open fun showState(){
        println("The $model is running at $velocity Km/h")
    }

    private fun hello(){
        println("New vehicle was created with name $model")
    }
}
```

---
# abstract
You can use abstract to declare a class if some method is abstract or it inherit from an abstract class
An abstract class cannot be instantiated (you cannot create objects of an abstract class). However, you can inherit subclasses from can them.

---
# override, open
You can over a function if its declared as abstract or open in the inherited class

---

# Encapsulation
```kotlin
private var _cabinTemperature : Float = 0.0f

var cabinTemperature : Float

get() {
    println("Someone is looking for the temperature in the cabin")
    return _cabinTemperature
}

set(value) {
    _cabinTemperature = value
    if (_cabinTemperature > 30) {
        _cabinTemperature = 30f
    }else if (_cabinTemperature < 15){
        _cabinTemperature = 15f
    }
}
```

---

# Initialization
```kotlin
var mySecondCar : Car = Car(4,  "Citroen")
vehicles.add(mySecondCar)
mySecondCar.cabinTemperature = 100f
println("Cabin temperature = ${mySecondCar.cabinTemperature}")
```

---

# Initialization
```kotlin
var vehicles = arrayListOf<Vehicle>()

vehicles.add(Car(4, "BMW"))
vehicles.add(Boat("Lamborghini"))
vehicles.add(Moto(2,"Kawasaki"))

for ( vehicle in vehicles){
    vehicle.accelerate()
}

for (vehicle in vehicles){
    vehicle.showState()
}
```

---

# Interface
It's like a class with signature method only
```kotlin
interface Wheels {
    fun checkNumberOfWheels ()
}
```

---

# Interface
```kotlin
class Moto : Vehicle, Wheels {

    var wheelsNumber : Int = 0

    constructor(wheelsNumber : Int, model: String) : super(model) {
        this.wheelsNumber = wheelsNumber
    }

    override fun accelerate () { velocity += 8 }
    override fun brake      () { velocity -= 1 }
    override fun checkNumberOfWheels() {
        println("This moto has $wheelsNumber wheels.")
    }
}
```

---
# Interface

```kotlin
for (vehicle in vehicles){
    vehicle.showState()
    if (vehicle is Wheels) {
        vehicle.checkNumberOfWheels()
    }
}
```

---

# Data Class
```kotlin
data class Person(val name: String, var age: Int)
```

---

# Object

```kotlin
object Test {
    private var a: Int = 0
    var b: Int = 1
    fun makeMe12(): Int {
        a = 12
        return a
    }
}

fun main(args: Array<String>) {
    val result: Int
    result = Test.makeMe12()
    println("b = ${Test.b}")
    println("result = $result")
}
```

---

# Companion object
```kotlin
class Car : Vehicle, Wheels {

// ….

    companion object{
        val FUEL_PRICE = 1.42f
        fun pricePerKm(kilometer : Float) : Float{
            return kilometer * FUEL_PRICE
        }
    }

}
println("50K costs ${Car.pricePerKm(50.0f)}€")
```

---

# extensions
```kotlin
fun Date.longDateString() : String  {
    val format = SimpleDateFormat("EEEE, dd MMMM yyyy - hh:mm:ss", Locale.getDefault())
    return format.format(this)
}

fun main(args: Array<String>) {
    val date = Date()
    println(date.longDateString())
}
```

---
# Scope Functions

---

# let
```kotlin
Person("Alice", 20, "Amsterdam").let {
    println(it)
    it.moveTo("London")
    it.incrementAge()
    println(it)
}
```

---

# let
```kotlin
    val str: String? = "Hello"
    //processNonNullString(str)       // compilation error: str can be null
    str?.let {
        println("let() called on $it")
        processNonNullString(it)      // OK: 'it' is not null inside '?.let { }'
        it.length
    }
```

---

# this or it
```kotlin
fun main() {
    val str = "Hello"
    // this
    str.run {   
    println("The receiver string length: $length")
    //println("The receiver string length: ${this.length}") // does the same
}

    // it
    str.let {
        println("The receiver string's length is ${it.length}")
    }
}
```

---

# With
```kotlin
val numbers = mutableListOf("one", "two", "three")
val firstAndLast = with(numbers) {
    "The first element is ${first()}," +
    " the last element is ${last()}"
}
println(firstAndLast)
```

---

# apply
```kotlin
val adam = Person("Adam").apply {
    age = 32
    city = "London"
}
println(adam)
```

---

# let and run
```kotlin
var str : String? =  null

str?.let {
    println("let() called on $it")
    processNonNullString(it)
    it.length
}?: run {
        str = "hello"
}
```

---

# Delegation
```kotlin
class Example {
    var p: String by Delegate()
}
import kotlin.reflect.KProperty

class Delegate {
    operator fun getValue(thisRef: Any?, property: KProperty<*>): String {
        return "$thisRef, thank you for delegating '${property.name}' to me!"
    }
    
    operator fun setValue(thisRef: Any?, property: KProperty<*>, value: String) {
        println("$value has been assigned to '${property.name}' in $thisRef.")
    }
}
```

---
# Android Introduction
Application Fundamentals

---
# Goal
Understand applications and their components
Concepts:
- activity,
- service,
- broadcast receiver,
- content provider,
- intent,
- Android Manifest

---
# Android OS Structure
![Android OS Structure](resources/architecture.jpg)

---
# **[Android App Life Cycle ](https://developer.android.com/guide/components/activities/activity-lifecycle)** 

![Android App Life Cycle](resources/activity_lifecycle.png)

---
# Applications
- Written in Java (it’s possible to write native code – will not - cover that here)
- Good separation (and corresponding security) from other - applications:
-- Each application runs in its own process
-- Each process has its own separate VM
-- Each application is assigned a unique Linux user ID – by default - files of that application are only visible to that application - (can be explicitly exported)

---
# Application Components
- Activities – visual user interface focused on a single thing a user can do
- Services – no visual interface – they run in the background
- Broadcast Receivers – receive and react to broadcast announcements
- Content Providers – allow data exchange between applications

---
# Activities
- Basic component of most applications
- Most applications have several activities that start each other as needed
- Each is implemented as a subclass of the base Activity class

---
# Activities – The View
- Each activity has a default window to draw in (although it may prompt for dialogs or notifications)
- The content of the window is a view or a group of views (derived from View or ViewGroup)
- Example of views: buttons, text fields, scroll bars, menu items, check boxes, etc.
- View(Group) made visible via Activity.setContentView() method.

---

# Services
Does not have a visual interface
Runs in the background indefinitely
Examples
Network Downloads
Playing Music
TCP/UDP Server
You can bind to a an existing service and control its operation

---

# Broadcast Receivers
Receive and react to broadcast announcements
Extend the class BroadcastReceiver
Examples of broadcasts:
Low battery, power connected, shutdown, timezone changed, etc.
Other applications can initiate broadcasts

---
# Content Providers
Makes some of the application data available to other applications
It’s the only way to transfer data between applications in Android (no shared files, shared memory, pipes, etc.)
Extends the class ContentProvider;
Other applications use a ContentResolver object to access the data provided via a ContentProvider

---
# Android Manifest
Its main purpose in life is to declare the components to the system
```xml
<?xml version="1.0" encoding="utf-8"?>
    <manifest . . . >
        <application . . . >
           <activity android:name="com.example.project.FreneticActivity"
                       android:icon="@drawable/small_pic.png"
                       android:label="@string/freneticLabel" 
                       . . .  >
             </activity>
             . . .    
     </application>
</manifest>

```
---
# Activities

```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val textViewHello : TextView = TextView(this)
        textViewHello.text = "Hello world!"

        val linearLayout = LinearLayout(this)
        linearLayout.addView(textViewHello)

        setContentView(linearLayout)
    }

}
```

---

# Activities
```kotlin
class MainActivity : AppCompatActivity() {
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val textViewHelloWorld = findViewById<TextView>(R.id.textViewHelloWorld)
        val buttonTranslate = findViewById<Button>(R.id.buttonTranslate)
        buttonTranslate.setOnClickListener {
            val dateNow = Date()
            textViewHelloWorld.text = dateNow.timeString()
        }

    }
}
```

---
# Activities – XML View
```kotlin
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity">

    <TextView
        android:id="@+id/textViewHelloWorld"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/buttonTranslate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:textSize="18sp"
        android:text="Traduzir"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textViewHelloWorld" />

</androidx.constraintlayout.widget.ConstraintLayout>
```


---
# Intents
An intent is an abstract description of an operation to be performed. It can be used with startActivity to launch an Activity, broadcastIntent to send it to any interested BroadcastReceiver components, and startService(Intent) or bindService(Intent, ServiceConnection, int) to communicate with a background Service.

---

# Intent example
```kotlin
val intentShare = Intent(Intent.ACTION_SEND)
intentShare.setType("text/plain")
intentShare.putExtra(Intent.EXTRA_SUBJECT,title)
intentShare.putExtra(Intent.EXTRA_TEXT,"http://www.google.com")
startActivity(Intent.createChooser(intentShare,"Partilhar"))
```

---

# Intent example
```kotlin
val callIntent = Intent(Intent.ACTION_CALL)
callIntent.data = Uri.parse("tel:" + "+351800253333")
startActivity(callIntent)
```

---

# Intents
// First  activity

```kotlin
val resultLauncher = registerForActivityResult(ActivityResultContracts.StartActivityForResult()) {
    if (it.resultCode == Activity.RESULT_OK) {
        val data = it.data
        data?.let {
            val qtd = it.extras?.getInt(ProductDetailActivity DATA_QTD)
            val productName = it.extras?.getString(ProductDetailActivity.   DATA_NAME)
            println("Product:${qtd} ${productName}")
            (...)
        }
    }
}

val intent = Intent(this@MainActivity, ProductDetailActivity::class.java)
intent.putExtra(ProductDetailActivity.DATA_QTD, productList[position].qtd)
intent.putExtra(ProductDetailActivity.DATA_NAME, productList[position].name)
intent.putExtra(ProductDetailActivity.DATA_POSITION, position)
resultLauncher.launch(intent)
```

---

# Intents
// Second activity

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    (...)
    intent.extras?.let {
        position = it.getInt(DATA_POSITION, -1)
        qtd = it.getInt(DATA_QTD)
        val name = it.getString(DATA_NAME)
    }
}

(...)
val intent = Intent()
intent.putExtra(DATA_QTD, qtd)
intent.putExtra(DATA_NAME , binding.editTextProductName.text.toString())
intent.putExtra(DATA_POSITION ,position)
setResult(Activity.RESULT_OK, intent)
finish()
(...)


```

---

# BroadcastReceivers
```kotlin
<receiver android:name="esrg.digitalsignage.standbyplayer.services.WifiReceiver" >
    <intent-filter>
        <action android:name="android.net.wifi.WIFI_STATE_CHANGED" />
    </intent-filter>
</receiver>
```
---

# BroadcastReceiver
```kotlin
fun sendBroadcastNotification(
    context: Context,
    title: String?,
    body: String?,
    type: String?) {
    val intent = Intent(BROADCAST_NOTIFICATION)
    intent.putExtra(TITLE, title)
    intent.putExtra(BODY, body)
    intent.putExtra(TYPE_NOTIFICATION, type)
    context.sendBroadcast(intent)
}
```

---

# BroadcastReceiver
```kotlin
private var notificationReceiver: NotificationReceiver? = null

internal inner class NotificationReceiver : BroadcastReceiver() {
    
    override fun onReceive(context: Context, intent: Intent) {
        val title = intent.getStringExtra(FirebaseMessaging.TITLE)
        val body = intent.getStringExtra(FirebaseMessaging.BODY)
        val action = intent.getStringExtra(FirebaseMessaging.TYPE_NOTIFICATION)
        …
    }
}
```

---

# BroadcastReceiver
```kotlin
override fun onResume() {
    super.onResume()
    if (notificationReceiver == null) {
        notificationReceiver = NotificationReceiver()
        this.registerReceiver(
            notificationReceiver,
            IntentFilter(FirebaseMessaging.BROADCAST_NOTIFICATION)
        )
        notificationReceiverActive = true
    }
}

override fun onPause() {
    super.onPause()
    if (notificationReceiver != null) {
        this.unregisterReceiver(notificationReceiver)
        notificationReceiver = null
        notificationReceiverActive = false
    }
}
```

---
# Services
```xml
<manifest ... >
  ...
  <application ... >
      <service android:name=".ExampleService" />
      ...
  </application>
</manifest>
```
---

# Services
```kotlin
class HelloService : Service() {

    private var serviceLooper: Looper? = null
    private var serviceHandler: ServiceHandler? = null
    private inner class ServiceHandler(looper: Looper) : Handler(looper) {

        override fun handleMessage(msg: Message) {
            try {
                Thread.sleep(5000)
            } catch (e: InterruptedException) {
                Thread.currentThread().interrupt()
            }
            stopSelf(msg.arg1)
        }
    }

    override fun onCreate() {
        HandlerThread("ServiceStartArguments", Process.THREAD_PRIORITY_BACKGROUND).apply {
            start()
            serviceLooper = looper
            serviceHandler = ServiceHandler(looper)
        }
    }

    override fun onStartCommand(intent: Intent, flags: Int, startId: Int): Int {
        Toast.makeText(this, "service starting", Toast.LENGTH_SHORT).show()
        serviceHandler?.obtainMessage()?.also { msg ->
            msg.arg1 = startId
            serviceHandler?.sendMessage(msg)
        }
        return START_STICKY
    }

    override fun onDestroy() {
        Toast.makeText(this, "service done", Toast.LENGTH_SHORT).show()
    }
}
```

---

# Services
```kotlin
    Intent(this, HelloService::class.java).also { intent ->
        startService(intent)
    }
```