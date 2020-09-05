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
