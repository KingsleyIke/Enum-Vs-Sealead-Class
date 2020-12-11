# Enum-Vs-Sealead-Class

Sealed classes can hold data specific to an instance. They are the most suitable to represent messages or classes with a concrete set of subclasses.

While Enums have supporting functions like valueOf, values or enumValues that makes them easier to iterate over or serialize. 
Just like classes, they can have custom methods or hold data, but always one per enum value. They are most suitable to represent a set of constant values.

ENUMS
When we had to represent a constant set of possible options, a classic choice was to use Enum. For instance, if our website offers a concrete set of 
payment methods, we can represent them in our service using the following enum class:

Enum can hold values that are always item-specific:

SAMPLE CODE
import java.math.BigDecimal

enum class PaymentOption {
    CASH,
    CARD,
    TRANSFER;

    var commission: BigDecimal = BigDecimal.ZERO
}

fun main() {
    val c1 = PaymentOption.CARD
    val c2 = PaymentOption.CARD
    print(c1 == c2) // true, because it is the same object

    c1.commission = BigDecimal.TEN
    print(c2.commission) // 10

    val t = PaymentOption.TRANSFER
    print(t.commission) // 0, because `commission` is per-item
}

SEALED CLASS
Another way to represent a concrete group of values is a sealed class. Sealed classes are abstract classes with a concrete number of subclasses all 
defined in the same file.

What sealed modifier does is that it is impossible to define another subclass of this class outside of the file. Thanks to that we are sure what are 
subclasses of a sealed class just by analyzing a single file. Kotlin compiler knows that as well and so in some contexts like when it can suggest options, 
and understand that all the possibilities were covered.

SAMPLE CODE
sealed class Response<out R>
class Success<R>(val value: R): Response<R>()
class Failure(val error: Throwable): Response<Nothing>()

fun handle(response: Response<String>) {
    val text = when (response) {
        is Success -> "Success, data are: " + response.value
        is Failure -> "Error"
    }
    print(text)
}

Summary
*Enum classes represent a concrete set of values, while sealed classes represent a concrete set of classes. Since those classes can be object declarations, 
 we can use sealed classes to a certain degree instead of enums, but not the other way around.

*The advantage of enum classes is that they can be serialized and deserialized out of the box. They have methods values() and valueOf. We can also get 
 enum values by type using enumValues and enumValueOf functions. Enums have ordinal and we can hold constant data by each item. They are perfect to 
 represent a constant set of possible values.
 
*The advantage of sealed classes is that they can hold instance-specific data. Each item can be either a class or an object (created using the object 
 declaration). They represent a set of alternative classes (sum type, coproduct). They are useful to define alternatives, Result that is either Success 
 or Failure, Tree that is either Leaf or Node, or JSON value that is either list, object, string, boolean, int or null. They are also great to define a 
 set of events or messages that might occur.
