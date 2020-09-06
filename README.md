# Swift Interview Prepration

## 1. Execution states of app:

### a. Not running: 
This means the app has not launched yet. Or the app has been terminated by the user. Also there is a possibility to the app has been terminated by the OS.

### b. Inactive: 
Inactive app state can be occurred while running the app if a phone call is received or activated siri.

### c. Active: 
This is the main execution state of an iOS application. The app is running on foreground and the UI is accessible. It receives any events and executes the code.

### d. Background: 
Once the app moved to background it will be transited to the Background state. In this state, still the app can execute the code and receive the events (Not UI events). But in a limited time period the OS automatically moves the app to the Suspended state and stops execution of code.

### e. Suspended: 
At this app state, your app remains on the memory. But not executing any code.
Since the app is not executing the code, the battery life is not affected by the application. But if any running app needs memory and the system is low on memory, the OS will terminate some suspended apps to free the memory.


## 2. AppDelegate Life Cycle Methods:

### Launch
### application:didFinishLaunchingWithOptions
This function is called by the OS when the launch process is almost done. (To launch the app, this function execution is need to be completed.) You can use this function and do the configurations you need, when the app is running.
Like,
- Create a Sqlite database for local data storage.
- Configure for data analytics.
- Configure for Firebase.

### applicationWillEnterForeground
This method is called after application: didFinishLaunchingWithOptions: or if your app becomes active again after receiving a phone call or other system interruption.

### applicationDidBecomeActive
This method is called after applicationWillEnterForeground: to finish up the transition to the foreground.

### Termination
### applicationWillResignActive
This method is called when the app is about to become inactive (for example, when the phone receives a call or the user hits the Home button).

### applicationDidEnterBackground
This method is called when your app enters in background state after becoming inactive. You have approximately five seconds to run any tasks you need to back things up in case the app gets terminated later or right after that.

### applicationWillTerminate
this method is called when your app is about to be purged from memory. Call any final cleanups here.


## 3. View Controller Life Cycle Methods:

### viewDidLoad:
This Method is loaded once in view controller life cycle. Its Called When all the view are loaded. You Can do Some common task in this method:
1.Network call which need Once.
2.User Interface
3.Others Task Those are Need to do Once
Note: This Method Call before the bound are defined and rotation happen.So its Risky to work view size in this method.

### viewWillAppear:
This Method is called every time before the view are visible to and before any animation are configured.

### viewDidAppear:
This Method is called after the view present on the screen. Usually save data to core data or start animation or start playing a video or a sound, or to start collecting data from the network This type of task good for this method.

### viewWillDisappear:
This method called before the view are remove from the view hierarchy. The View are Still on view hierarchy but not removed yet . any unload animations haven’t been configured yet. Add code here to handle timers, hide the keyboard, cancel network requests, revert any changes to the parent UI. Also, this is an ideal place to save state.

### viewDidDisappear:
This method is called after the VC’s view has been removed from the view hierarchy. Use this method to stop listening for notifications or device sensors.


## 4. Class and Struct:

### Similarities:
- Defines properties to store values.
- Defines methods to provide functionality.
- Defines initializers to set up their initial state.
- Conforms to protocols.

### Differences:
- Inheritance enables one class to inherit the characteristics of another.
- Deinitializer enables an instance of a class.
- Reference counting allows more than one reference to a class instance.
- Class is reference type but struct is value type.
- Instance of a class is stored in heap memory and instance of struct is stored in stack memory.
- Struct is faster than class.


## 5. Optional:

A type that represents either a wrapped value or nil, the absence of a value.

```ruby
var value: String?
```

### Optional Binding: (Conditional Unwrapping)
To conditionally bind the wrapped value of an Optional instance to a new variable, use one of the optional binding control structures, including if let, guard let, and switch.

```ruby
if let starPath = imagePaths["star"] {
    print("The star image is at '\(starPath)'")
} else {
    print("Couldn't find the star image")
}
// Prints "The star image is at '/glyphs/star.png'"
```

```ruby
 guard let starPath = imagePaths["star"] else {
     return
  }
 print("The star image is at '\(starPath)'")
```

### Optional Chaining:
To safely access the properties and methods of a wrapped instance, use the postfix optional chaining operator (postfix ?). The following example uses optional chaining to access the hasSuffix(_:) method on a String? instance.

```ruby
if imagePaths["star"]?.hasSuffix(".png") == true {
    print("The star image is in PNG format")
}
// Prints "The star image is in PNG format"
```

### Using the Nil-Coalescing Operator:
Use the nil-coalescing operator (??) to supply a default value in case the Optional instance is nil. Here a default path is supplied for an image that is missing from imagePaths.

```ruby
let defaultImagePath = "/images/default.png"
let heartPath = imagePaths["heart"] ?? defaultImagePath
print(heartPath)
// Prints "/images/default.png"
```

The ?? operator also works with another Optional instance on the right-hand side. As a result, you can chain multiple ?? operators together.

```ruby
let shapePath = imagePaths["cir"] ?? imagePaths["squ"] ?? defaultImagePath
print(shapePath)
// Prints "/images/default.png"
```

### Unconditional Unwrapping: (Implicitly Unwrapping)
When you’re certain that an instance of Optional contains a value, you can unconditionally unwrap the value by using the forced unwrap operator (postfix !). For example, the result of the failable Int initializer is unconditionally unwrapped in the example below.

```ruby
let age: Int! = 20
print(age)
// Prints 20
```

You can also perform unconditional optional chaining by using the postfix ! operator.

```ruby
let isPNG = imagePaths["star"]!.hasSuffix(".png")
print(isPNG)
// Prints "true"
```

Unconditionally unwrapping a nil instance with ! triggers a runtime error.

### Unwrapping via Type Casting:
In this way, Sometimes different types of values ​​can be defined during the runtime of the application. If you don’t be careful, your application may be crash.

```ruby
var userData: Any? = 1

if userData as? String != nil {
    print("userData is defined as a String.")
} else if userData as? Int != nil {
    print("userData is defined as an Integer.")
}
```

### Forced Unwrapping:
You can unwrap your Optional variable with “!” operator but it’s a less safe wrapping way, you have to be sure of variable contains value or not. If you do not use the forcibly unwrapping method in the right place, your application may be crash.

```ruby
var moviesCount: Int?
print(moviesCount!)
// Fatal error: Unexpectedly found nil while unwrapping an Optional value
```

## 6. Delegate: 
A delegate is an object that acts on behalf of, or in coordination with, another object when that object encounters an event in a program.

## 7. Protocol:
A protocol defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality. The protocol can then be adopted by a class, structure, or enumeration to provide an actual implementation of those requirements. Any type that satisfies the requirements of a protocol is said to conform to that protocol.

```ruby
protocol SomeProtocol {
    var name: String { get set }
    var email: String { get }
    static var address: String { get }
    static func someTypeMethod()
    func anyMethod()
}

class MyClass: SomeProtocol {
    var email: String {
        return "ayush@gmail.com"
    }
    
    func anyMethod() {
        // write some code
    }
}
```

### Optional Protocol Methods:
It is not necessary to implement that method if we were not going to use it. Swift protocols on their side do not allow optional methods. But if you are making an app for macOS, iOS, tvOS or watchOS you can add the @objc keyword at the beginning of the implementation of your protocol and add @objc follow by optional keyword before each methods you want to be optional.

```ruby
@objc protocol SomeProtocol {
    @objc optional var age: Int { get }
    @objc optional func getValue()
    func anyMethod()
}

class MyClass: SomeProtocol {    
    func anyMethod() {
        // write some code
    }
}
```

## 8. Tuples:
Tuples enable you to create and pass around groupings of values. You can use a tuple to return multiple values from a function as a single compound value.

There are two types of Tuple:
1. Named Tuple:
In Named tuple we assign individual names to each elements.

```ruby
// Define it like:

let nameAndAge = (name:"Midhun", age:7)

// Access the values like:

nameAndAge.name
nameAndAge.age
```

2. Unnamed Tuple:
In unnamed tuple we don't specify the name for it's elements.

```ruby
// Define it like:

let nameAndAge = ("Midhun", 7)

// Access the values like:

nameAndAge.0
nameAndAge.1
```

### Difference between Tuples & Dictionary:
- If you need to return multiple values from a method you can use tuple.
- Tuple won't need any key value pairs like Dictionary.
- A tuple can contain only the predefined number of values, in dictionary there is no such limitation.
- A tuple can contain different values with different datatype while a dictionary can contain only one datatype value at a time.
- Tuples are particularly useful for returning multiple values from a function. A dictionary can be used as a model object.

## 9. Generics:
Generic code enables you to write flexible, reusable functions and types that can work with any type, subject to requirements that you define. You can write code that avoids duplication and expresses its intent in a clear, abstracted manner.

Example:
```ruby
func getValue<T>(arr: [T]) -> T {
    return arr[0]
}

print(getValue(arr: [1, 2, 3])) // prints 1
print(getValue(arr: ["Car", "Bat", "Mobile"])) // prints Car
print(getValue(arr: [1.1, 2.1, 3.1])) // prints 1.1
```

## 10. Dependency Injection:
- Dependency Injection is often used with the intention of writing code that is loosely coupled, and thus, easier to test.

- Separation of concerns:
- Dependency injection allows us to understand our code in a much clearer way and separates our concerns. When we use dependency injection, we can see that our objects are responsible for managing and handling the given dependency.

- Testing:
- Dependency injection is great for testing.

- Loosely Coupled:
- In computing and systems design a loosely coupled system is one in which each of its components has, or makes use of, little or no knowledge of the definitions of other separate components.

## 11. Access Control:
Access control restricts access to parts of your code from code in other source files and modules. This feature enables you to hide the implementation details of your code, and to specify a preferred interface through which that code can be accessed and used.

- Open access and public access enable entities to be used within any source file from their defining module, and also in a source file from another module that imports the defining module. You typically use open or public access when specifying the public interface to a framework. 
- Internal access enables entities to be used within any source file from their defining module, but not in any source file outside of that module. You typically use internal access when defining an app’s or a framework’s internal structure.
- File-private access restricts the use of an entity to its own defining source file. Use file-private access to hide the implementation details of a specific piece of functionality when those details are used within an entire file.
- Private access restricts the use of an entity to the enclosing declaration, and to extensions of that declaration that are in the same file. Use private access to hide the implementation details of a specific piece of functionality when those details are used only within a single declaration.

### Difference between Open and Public:
- An open class is accessible and subclassable outside of the defining module. 
- An open class member is accessible and overridable outside of the defining module.
