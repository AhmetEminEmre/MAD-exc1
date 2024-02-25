# MAD - Exercise 01
## Tasks
* Watch the Kotlin Crashcourse Video in Moodle or complete the tutorials **[Introduction to programming in Kotlin](https://developer.android.com/courses/pathways/android-basics-compose-unit-1-pathway-1)** and **[Kotlin fundamentals](https://developer.android.com/courses/pathways/android-basics-compose-unit-2-pathway-1
)**.
* Answer the questions inside this Readme.md file and push it to your repository.
* Submit your coding solution of the Number Guessing Game inside the repository.
* Submit the link to your repository in Moodle.

## Questions
### Describe how Kotlin handles null safety. What are nullable types and non-null types in Kotlin? (0,5 points)

<span style="color:blue">Quelle: https://developer.android.com/codelabs/basic-android-kotlin-compose-nullability?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-2-pathway-1%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-nullability#1 </span>

Kotlin handles null safety by introducing nullable and non-nullable types. This means that variables in Kotlin cannot hold a null value by default and can only do so if explicitly declared as nullable.

Non-nullable types:

Non-nullable types in Kotlin are those that cannot contain a null value. When you declare a variable of this type, you must assign a value to it immediately.
For example, when declaring a favoriteActor variable of type String:

```kotlin 
// example code snippet
val favoriteActor: String = "Sandra Oh" 
```
In this case, favoriteActor cannot be set to null since String is a non-nullable type. Attempting to assign favoriteActor = null would result in a compilation error.


Nullable types:

Nullable types are those that can hold a null value. In Kotlin, they are marked with a question mark ? after the type name. 
For instance, if you want the favoriteActor variable to be able to be null, you would declare it like this:

```kotlin 
// example code snippet
var favoriteActor: String? = "Sandra Oh" 
```
Now, favoriteActor can be set to null without causing a compilation error:
```kotlin 
// example code snippet
favoriteActor = null
```

### What are lambda expressions and higher order functions in Kotlin? Why would you store a function inside a variable? (0,5 points)

<span style="color:blue">Quelle: https://developer.android.com/codelabs/basic-android-kotlin-compose-function-types-and-lambda?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-2-pathway-1%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-function-types-and-lambda#4</span>

Lambda expressions in Kotlin are essentially anonymous functions that you can treat as values – you can store them in variables, pass them as arguments to other functions, and return them from functions. 
They provide a concise way to represent function implementations without declaring a formal function using the "fun" keyword.

Example:

```kotlin 
// example code snippet
val trick = { println("No treats!") }
```
In this example, trick is a variable that stores a lambda expression. This lambda takes no parameters (() implied) and returns no value (Unit implied), but it has a side effect: it prints "No treats!" to the console


Higher-order functions are functions that take functions as parameters, or return a function. This allows for more abstract and flexible code. 
For example, a function that returns another function based on a condition:

```kotlin 
// example code snippet
fun performOperation(x: Int, y: Int, operation: (Int, Int) -> Int): Int {
    return operation(x, y)
}
```
In this example, performOperation is a higher-order function because it takes another function, operation, as a parameter. This operation parameter is a function that takes two integers and returns an integer.

Storing a function inside a variable makes your code more flexible and easier to read. It allows you to change how parts of your app work without rewriting them entirely. This approach is handy for tasks like sorting or responding to user actions, where you might want to switch between different behaviors without changing the overall code structure. It simplifies your code, making it more adaptable and reusable.

### Provide a solution for the following number guessing game inside `App.kt`. (3 points)

## Number Guessing Game in Kotlin
The game is a simple number guessing game. The task is to generate a random, max 9-digit, number. The number must **not contain repeating digits**. Valid digits are 1-9.
Ask the user to guess the max 9-digit number. The game is finished when the user guesses the correct digits in the correct order.
In each round, the user gets feedback about the number of correct digits and the number of correct digits in the correct position.
The output should be in the format "n:m", where "n" is the number of digits guessed correctly regardless of their position, 
and "m" is the number of digits guessed correctly at their correct position. Here are some examples:

This example shows the game flow with 4-digits to guess (the default argument)

Generated number: 8576
-	User input: 1234, Output: 0:0
-	User input: 5678, Output: 4:1
-	User input: 5555, Output: 1:1
-	User input: 3586, Output: 3:2
-	User input: 8576, Output: 4:4 -> user wins

Take a look into the provided code structure in `src/main/kotlin/App.kt`. Implement the following methods (lambda expressions):
- _playNumberGame(digitsToGuess: Int = 4)_ (1 point): The main game loop that handles user input and game state. Make use of _generateRandomNonRepeatingNumber_ and _checkUserInputAgainstGeneratedNumber_ here. This function also utilizes a default argument 
- _generateRandomNonRepeatingNumber_ (1 point): A lambda expression that generates a random number with non-repeating digits of a specified length.
- _checkUserInputAgainstGeneratedNumber_ (1 point): A lambda expression that compares the user's input against the generated number and provides feedback.

``CompareResult.kt`` This class is a data structure which helps with bundling the result of the comparison of the user input and the generated number. Look at the toSting() and use it in your output.

Run the project with `./gradlew run` and test your implementation with the provided tests in `src/test/kotlin/AppTest.kt` with `./gradlew test`.

# Project Structure
The project is structured into two main Kotlin files:

**App.kt**: Contains the main game logic and functions.

**AppTest.kt**: Contains unit tests for the various functions in App.kt.

