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


