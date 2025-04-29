# KOTLIN
  
## Variables
  
```kotlin
// 1
val question = "What's your name?"
// 2 
val question: String = "What's your name?"
// 3 
var question: String = "What's your name?"
```
   


val = immuable, doit donc être initialisés, mais pas forcement à la declaration.   
   
```kotlin
var message: String? = "My message can possibly be null!"
```
   
   
Variable de type string:   
```kotlin
val name = "Phil"
print("Hello $name")
```

   
const  précédant le mot-clé  val  nous permet de définir une constante dont la valeur sera connue au moment de la compilation.   
définir une variable comme étant "initialisable plus tard" dans votre code grâce au mot-clé  lateinit.   

## Class

Déclarer   
   
```kotlin
class User(var email: String, var password: String, var age: Int)
```
   
Instancier   
   
```kotlin
val user = User("hello@gmail.com", "azerty", 27)
```
   
Cas d'usage   
```kotlin
val user = User("hello@gmail.com", "azerty", 27)
user.email // Getter
user.email = "new_email@gmail.com" // Setter
```
   
Modifier une class   
```kotlin
class User(email: String, var password: String, var age: Int){
    var email: String = email
        get() { 
            println("User is getting their email."); 
            return field 
        }
        set(value) { 
            println("User is setting their email"); 
            field = value 
        }
}
```
   
Explication de 'field' (backing field):
[backing field](https://kotlinlang.org/docs/properties.html#backing-fields)   
   
```kotlin
class User(var email: String, private var password: String, var age: Int)
```
   
## Conditions
   
```kotlin
val result = if (a > b) a else b
```
   
### When (switch)   
   
```kotlin
var apiResponse = 404

when (apiResponse) {
    200 -> print("OK")
    404 -> print("NOT FOUND")
    401 -> print("UNAUTHORIZED")
    403 -> print("FORBIDDEN")
    else -> print("UNKNOWN")
}
```
   
### Enumération
   
```kotlin
enum class ApiResponse {
    OK,
    NOT_FOUND,
    UNAUTHORIZED,
    FORBIDDEN,
    UNKNOWN;
}
```
   
[Control Flow](https://kotlinlang.org/docs/control-flow.html)   
   
## Iteration et bpoucle
   
### while
   
```kotlin
// While 
while (isARainyDay) {
    println("I don't love rain...")
}

// Do While
do {
    println("I don't love rain...")
} while (isARainyDay)
```
   
### for...in
   
```kotlin
val names = listOf("Jake Wharton", "Joe Birch", "Robert Martin");

for (name in names) {
    println("This developer rocks: $name");
}
```
   
```kotlin
for (i in names.indices) {
    println("This developer with number $i rocks: ${names[i]}")
}

for ((index, value) in names.withIndex()) {
    println("This developer with number $index rocks: $value")
}
```

   
```kotlin
for (i in 0..3) println(i)
```

   
** Avec instruction   
```kotlin
for (i in 10 downTo 1 step 2) {
    println("Index is: $i")
}
```

   
### Liste
   
```kotlin
// listOf
val listOfNames = listOf("Jake Wharton", "Joe Birch", "Robert Martin")
listOfNames[0] // => Jake Wharton
listOfNames[0] = "James Deen" // => ERROR! List is immutable

// mutableListOf
val listOfNames = mutableListOf("Jake Wharton", "Joe Birch", "Robert Martin")
listOfNames[0] // => Jake Wharton
listOfNames[0] = "James Deen" // => SUCCESS!
```

   
## Smart Cast
   
### Rechercher le type
```kotlin
private fun getDefaultSize(anyObject: Any): Int {
    // Vérification du type 
    if (anyObject is String) {
        return anyObject.length
    // Vérification du type 
    } else if (anyObject is List<*>) {
        return anyObject.size
    }
    return 0
}
```

** Avec when:   
```kotlin
private fun getDefaultSize(anyObject: Any) = when (anyObject) {
    is String -> anyObject.length
    is List<*> -> anyObject.size
    else -> 0
}
```
   
### Unsafe Cast
  
```kotlin
val anyObject: Any = "Hello, Kotlin students!"
val message = anyObject as String
print(message)
```
   
[Type checks and casts﻿](https://kotlinlang.org/docs/typecasts.html)   
   
## Les Exceptions ( [Exception](https://kotlinlang.org/docs/exceptions.html) )
   
```kotlin
private fun subtractNumber(a: Int, b: Int) = if (a >= b) a - b else throw Exception("a is smaller than b!")
   
// Exception non gérée 
subtractNumber(20,10) 
   
// Exception gérée 
try{
    subtractNumber(20,10)
} catch(e: Exception) {
    print(e.message)
}
```
   
#### Operateur elvis ( [Elvis Operator](https://kotlinlang.org/docs/null-safety.html#elvis-operator) )
   
```kotlin
// ?: Opérateur Elvis
val password = user.password ?: throw IllegalArgumentException("Password required")
```

   




