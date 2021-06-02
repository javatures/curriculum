### Non-Access Modifiers

Java also has **non-access** modifiers which can be placed on various class members:
* `static` - denotes \"class\" scope, meaning the member resides on the class itself, not object instances.
  * `static` variables can be accessed through the class, e.g. `MyClass.staticVariable`
  * `static` methods can be called directly without needing an instance of the class, e.g. `MyClass.someMethod()`
* `final`
  * when applied to a variable, it means the variable **cannot be re-assigned**
  * when applied to a class, it means the class **cannot be extended**
  * when applied to a method, it means the method **cannot be overriden**
* `abstract`
  * when applied to a class, the class **cannot be instantiated** directly (instead, it should be *inherited*)
  * when applied to a method, only the method signature is defined, not the implementation. Also, the class where the method resides must also be abstract. Concrete subclasses **must implement the abstract method**.
* `synchronized` - relevant to threads and preventing deadlock phenomena (discussed in a separate module)
* `transient` - marks a variables as non-serializable, meaning it will not be persisted when written to a byte stream (discussed in another module)
* `volatile` - marks a variable to never be cached thread-locally. Obscure, rarely-used keyword.
* `strictfp` - restricts floating point calculations for portability. Obscure, rarely-used keyword.

Below is a class with various class members which have different modifiers associated with them:
```
package com.revature.mypackage;

public class Example {
        // <-- this notation specifies a comment
\tpublic boolean a; // this variable can be accessed anywhere, on an object of type Example
\tprotected byte b; // accessible within com.revature.mypackage or subclasses of Example
\tstatic int c; // class scope with default access
\tprivate String d; // can only be accessed within this class
\t
\tpublic static void main(String[] args) {
    \t\tExample myExample = new Example();
\t\tmyExample.printValues();
\t\t// prints out the default values:
\t\t// The value of a is: false
\t\t// The value of b is: 0
\t\t// The value of c is: 0
\t\t// The value of d is:
\t}
\t
\tpublic void printValues() {
    \t\tSystem.out.println(\"The value of a is: \" + a);
\t\tSystem.out.println(\"The value of b is: \" + b);
\t\tSystem.out.println(\"The value of c is: \" + c);
\t\tSystem.out.println(\"The value of d is: \" + d);
\t}
}
```