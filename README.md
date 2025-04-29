# KOTLIN
  
## Variables
  
```
// 1
val question = "What's your name?"
// 2 
val question: String = "What's your name?"
// 3 
var question: String = "What's your name?"```

val = immuable, doit donc être initialisés, mais pas forcement à la declaration.   
   
```var message: String? = "My message can possibly be null!"```   
   
Variable de type string:   
```val name = "Phil"
print("Hello $name")```   
   
const  précédant le mot-clé  val  nous permet de définir une constante dont la valeur sera connue au moment de la compilation.   
définir une variable comme étant "initialisable plus tard" dans votre code grâce au mot-clé  lateinit.   


## Class

Déclarer   
   
```class User(var email: String, var password: String, var age: Int)``` 
   
Instancier   
   
```val user = User("hello@gmail.com", "azerty", 27)```   
   
Cas d'usage   
```val user = User("hello@gmail.com", "azerty", 27)
user.email // Getter
user.email = "new_email@gmail.com" // Setter```   
   
Modifier une class   
```class User(email: String, var password: String, var age: Int){
    var email: String = email
        get() { 
            println("User is getting their email."); 
            return field 
        }
        set(value) { 
            println("User is setting their email"); 
            field = value 
        }
}```   
   
Explication de 'field' (backing field):
[backing field](https://kotlinlang.org/docs/properties.html#backing-fields)   
   
```class User(var email: String, private var password: String, var age: Int)```   
   
## Conditions
   
```val result = if (a > b) a else b```   
   
### When (switch)   
   
```var apiResponse = 404

when (apiResponse) {
    200 -> print("OK")
    404 -> print("NOT FOUND")
    401 -> print("UNAUTHORIZED")
    403 -> print("FORBIDDEN")
    else -> print("UNKNOWN")
}```   
   
### Enumération
   
```enum class ApiResponse {
    OK,
    NOT_FOUND,
    UNAUTHORIZED,
    FORBIDDEN,
    UNKNOWN;
}```   
   
[Control Flow](https://kotlinlang.org/docs/control-flow.html)   
   
## Iteration et bpoucle
   
### while
   
```// While 
while (isARainyDay) {
    println("I don't love rain...")
}

// Do While
do {
    println("I don't love rain...")
} while (isARainyDay)```   
   
### for...in
   
```val names = listOf("Jake Wharton", "Joe Birch", "Robert Martin");

for (name in names) {
    println("This developer rocks: $name");
}```   
   
```for (i in names.indices) {
    println("This developer with number $i rocks: ${names[i]}")
}

for ((index, value) in names.withIndex()) {
    println("This developer with number $index rocks: $value")
}```   
   
```for (i in 0..3) println(i)```   
   
** Avec instruction   
```for (i in 10 downTo 1 step 2) {
    println("Index is: $i")
}```   
   
### Liste
   
```// listOf
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
```private fun getDefaultSize(anyObject: Any): Int {
    // Vérification du type 
    if (anyObject is String) {
        return anyObject.length
    // Vérification du type 
    } else if (anyObject is List<*>) {
        return anyObject.size
    }
    return 0
}```   
** Avec when:   
```private fun getDefaultSize(anyObject: Any) = when (anyObject) {
    is String -> anyObject.length
    is List<*> -> anyObject.size
    else -> 0
}```   
   
### Unsafe Cast
  
```val anyObject: Any = "Hello, Kotlin students!"
val message = anyObject as String
print(message)```   
   
[Type checks and casts﻿](https://kotlinlang.org/docs/typecasts.html)   
   
## Les Exceptions ( [Exception](https://kotlinlang.org/docs/exceptions.html) )
   
```private fun subtractNumber(a: Int, b: Int) = if (a >= b) a - b else throw Exception("a is smaller than b!")```   
   
```// Exception non gérée 
subtractNumber(20,10)```   
   
```// Exception gérée 
try{
    subtractNumber(20,10)
} catch(e: Exception) {
    print(e.message)
}```   
   
#### Operateur elvis ( [Elvis Operator](https://kotlinlang.org/docs/null-safety.html#elvis-operator) )
   
èèè// ?: Opérateur Elvis
val password = user.password ?: throw IllegalArgumentException("Password required")```   
   




