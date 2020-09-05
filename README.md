# Swift Interview Prepration

## 1. Execution states of app

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

### application:didFinishLaunchingWithOptions

### applicationWillEnterForeground

### applicationDidBecomeActive

### applicationWillResignActive

### applicationDidEnterBackground

### applicationWillTerminate
