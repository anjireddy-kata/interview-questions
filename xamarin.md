## My Favourite Xamarin Interview Questions

### Q1: What is Xamarin?
Ans:
Xamarin is an open source app platform from Microsoft for building modern & performant iOS and Android apps with C# and .NET. Xamarin runs in a managed environment that provides conveniences such as memory allocation and garbage collection. 

Xamarin enables developers to share an average of 90% of their application across platforms. This pattern allows developers to write all of their business logic in a single language (or reuse existing application code) but achieve native performance, look, and feel on each platform.

### Q2: Who Xamarin is for
Xamarin is for developers with the following goals:

Share code, test and business logic across platforms.
Write cross-platform applications in C# with Visual Studio.

### Q3: What is the advantage of Xamarin Development?
Ans:
#### Advantages:
One of the best parts of Xamarin is that it contains about 90% of the reusable code and it can be also recycled for the development of the apps on the various platforms.
In Xamarin, it is possible to access each and every native API. For these reasons only it is possible to completely use the Native UI, Bluetooth and SDKs.
Maintainance and the updating of the apps that are build using the Xamarin require less work.
With the help of the Xamarin, a developer can create apps for mobile and desktop experiences simultaneously.
Xamarin takes the advantages of the native framework and usually, it takes 1 to 3 days for the iOS and the Android platform to catch up on the latest features.

#### Disadvantages:
Ans:
Slightly delayed support for the latest platform update
Limited access to the open sources libraries
There are a few problems with the Xamarin Ecosystem
One will require basic knowledge of the native language
Not suitable for the apps that are of heavy graphics
Larger app size
Compatibility issues with the third party libraries and the tools

### Q4: What are the development approaches in Xamarin?
Ans:
Xamarin has two approaches for app development. These are

Xamarin.Forms: 
Xamarin.Forms is a framework which is used to build the user interface in the mobile application.

Forms are the choices for the developers who want to create one application for all the separate mobile platforms, which are Windows, iOS, and Android. Xamarin.Forms allows the developer to create just one UI which can be used across all platforms like Android, iOS, and Windows.

Xamarin Native: This approach is used in those scenarios when we want to create a separate version of the same App for different platforms. Developers can use Xamarin.iOS, Xamarin.Android and Xamarin.Windows libraries to create the applications for each particular platform.

### Q5: What is XAML and what are the advantages of XAML?
Ans:
XAML stands for the Extensible Application Markup Language. XAML allows you to define the user interface in Xamarin. Forms application use the markup language rather than code. i.e. In xamarin, you use XAML to define the UI and .NET code to define the business logic.

Advantages:
XAML gives a clean division between an application and its code. Thus, it enables a clear developer-designer workflow.
XAML has the parent-child hierarchy of user-interface objects with greater visual simplicity.

### Q6: What are the different kinds of pages are present in the Xamarin.forms?
The following are some of the different pages that are available in the Xamarin.forms:

##### Content page – this type of the page displays a single view, often a container such as a stack layout or the scroll view.
##### Master-Detail page – this type of page manages two types of panes of information.
##### Navigation page – a page that manages the navigation and the user experiences as a stack of other pages
##### Tabbed page – this page allows the navigation of the children pages using the tab.
##### Templated page – a page that helps to display the full page content with a control template and the base class for the content page.
##### Carousel page – a page allowing the swipe gestures between the subpages such as a gallery.

### Q7: Whatis databinding and what are the different types of binding modes available in Xamarin?
Ans:
Data binding is the technique of linking properties of two objects so that changes in one property are automatically reflected in the other property. i.e. In xamarin, using Data binding you can establish a connection between the Application user interface and an Application logic.

The following are the different types of data binding modes in Xamarin:

Default
One way – changes in the source affects the target
One way to the source – changes in the target affect the source
Two way – changes in the source and target affect each other
OneTime – data goes from source to target, but only when the BindingContext changes (new with Xamarin.Forms 3.0)
https://docs.microsoft.com/en-us/xamarin/xamarin-forms/app-fundamentals/data-binding/binding-mode

### Q8: What are the different ways to share the code in Xamarin?
Ans:

.NET Standard Libraries
Shared Projects
Portable Class Libraries (Deprecated)

###### .NET Standard Libraries
.NET Standard Libraries is a way to share common code over multiple runtimes. .NET Standard is a set of specifications which various .NET runtimes adhere to and hence code written for one version of .NET Standard works on multiple versions of .NET runtimes like .NET Core, Mono, etc.  You can write your code and compile it into .NET Class Library and share it with others.

###### Using Shared Projects

Shared Projects are the usual .NET application projects that contain code files and assets. Shared Projects are meant to be included in other projects and help in code reuse. It is a code level sharing technique.

A cross-platform application that supports iOS, Android, and Windows would require an application project for each platform and a separate Shared Project for the code common to all.

So, if you are creating a cross-platform app for Android, iOS, and Windows, you will usually have the following projects

Shared Project – the Shared Project that contains the code which is common for all platforms viz iOS, UWP, Android
AppAndroid – the Xamarin.Android project that specifically calls the underlying .NET APIs exposed for Android
AppiOS – Xamarin.iOS application project that specifically calls the underlying .NET APIs exposed for iOS
AppWindows – Windows application project that utilizes exposed Windows APIs and specific to UWP (Universal Windows Platform)
A Shared Project is not directly compiled. In other words, no DLL file is produced in the compilation process. Instead, the files are compiled into the same DLL as the project that references it. This way, it is possible to write blocks of platform-specific code in the Shared Project that will only be compiled by the specific platform.

### Q9: What are custom renders in xamarin.Forms?
Custom renderers allow the Generic Xamarin.Forms control to be customized in behavior and look as per the platform they are going to be used on. This enables developers to give a native look and behavior to the otherwise Generic Xamarin.Forms Control.  

Xamarin Forms controls are NOT rendered directly on the native platform. Every Xamarin.Forms control has an accompanying renderer for each platform that creates an instance of a native control. The properties from the Xamarin Forms control are translated across to the native control, then the native control is placed in the native layout, which then gets rendered by the platform.  

Custom Renderers allow developers to customize the appearance and/or behavior of the control by writing their custom classes. Custom Renderers can be defined to have a custom behavior or appearance for one platform while allowing the default behavior on other platforms or they can be defined for each platform and provide customization for each different platform like iOS, Android, and the Universal Windows Platform (UWP).  If instead of changing the complete behavior and appearance only some trivial changes are required then 'Effects' can be used as an alternative.

### Q10: What are effects and when should they be used?
Effects, like Custom Renderers, allow a developer to customize controls for a specific platform. Effects are preferred over Custom Renderers when small styling changes are required instead of a complete layout or behavior change. Custom Effects are created for platform-specific projects by extending the base class PlatformEffect. Once created, they can be attached to the control it is meant for.  

Effects don't have any type related information about the control they are attached to and hence if they are specified with a wrong control they should gracefully degrade. Effects are reusable and can be parameterised to extend its reusability.  

### Q11: Lifecycle of xamarin App?
The lifecycle of an app contains the sequence of methods that are called since the time the app is launched until the time it is in the memory. The Lifecycle methods allow developers to write code for initialization or logic or transition so that the app components are initialized or show a specific behavior as and when they transit from one state to another. The developer may want to save state, initialize graphical components with data or reset apps state or free memory during these App methods.

The various life cycle methods of XamarinForms Apps are:

OnStart: when the application initializes onStart is called. It is the best place to initialize objects
OnSleep: Once the application goes to the background, the state is called ‘resume’. The app does not die here rather is kept in memory but with reduced priority. OnSleep() is similar to OnPause() in Android
OnResume: OnResume is called when the application is resumed, i.e after being sent to the background. Similar to OnResume on Android.

### Q12: What are behaviours in xamarin.forms?
Ans:
Behaviors are a special technique that lets us add functionality to your UI control without having to subclass the control. Behaviors are implemented to code and attached to the controls written in XAML or code.  Behaviors interact directly with the APIs exposed by the controls and hence they can be packaged with the control and reused across various applications. Behaviors allow adding new functionality like e.g. an Email Validator to an Entry that accepts Email as user input. Another use case could be a spelling checker with the Entry that helps you correct your spelling while typing. Other typical uses of behaviors are to add an effect to control or to control the control animation.

Behaviors are usually of following types:

###### Xamarin.Forms behaviors 
classes that derive from the Behavior or Behavior<T> class where T is the type of control to which the behavior should apply
  
###### Attached behaviors
These are static classes with one or more attached properties
###### Reusable Behaviors 
Behaviors that are reusable across more than one application.

Behaviors are written for a specific control type ), and hence,  they are supposed to be added only to a compatible control. Attempting to attach a behavior to an incompatible control will result in an exception being thrown.

### Q13: What is a trigger and what are the different types of triggers?
Triggers allow the developer to specify actions declaratively in XAML to change the appearance of controls based on events or property changes. For eg, you may want to change the appearance of a button when it is in pressed state vs when it is not pressed. A trigger can be directly assigned to control.

There are namely four types of triggers:

Property Trigger: Property Trigger comes into action when the value of the property of a control is assigned a value
Data Trigger: It uses data binding to associate changes for some other control. When there are changes to another control, Data Trigger triggers changes in the control
Event Trigger: An Event trigger causes an action to happen when an event takes place
Multi-Trigger: This is a special type of trigger which gets triggered when multiple trigger conditions get satisfied resulting in the raising of this trigger.

### Q14: What is info.plist in xamarin?
To provide a seamless experience to users iOS provides metadata to the system in the form of info.plist (information property list file). This metadata is used by the system to identify the app, document types it supports, and to facilitate the launch of apps.

The property list can be accessed by the system at runtime. It containskey-value pairs. These key-value pairs describe the various behaviors and configuration options for the app. For every app, the Xcode provides info.pList files with default key values which can be later edited to suit the needs of the application

The various types of keys defined in info.plist files are:

Core Foundation Keys: The keys specified in use the prefix 'CF' to distinguish them with other keys. They provide information related to bundles which help in loading them and knowing their content
Launch Services Keys: They use the prefix LS to distinguish them from other keys. They provide metadata related to the launch time behavior of the app
Cocoa Keys: Cocoa keys use the prefix NS to distinguish them from other keys. Cocoa keys define metadata related to Cocoa Touch Apps
iOS Keys: UIKit keys use the prefix UI to distinguish them from other keys
App Extension Keys: App extensions enable you to provide features to other apps in iOS and macOS. App Extension Keys provide system information about an app extension's capabilities and intents.

### Q15: What is NSUserDefault? How to use NSUserDefault in Xamarin.ios?
Sometimes a developer has a requirement to store some basic user data dealing with user settings and app configuration. There are plenty of ways that Xamarin.iOS provides to save this data in your app. One such way is through NSUserDefaults.

The NSUserDefaults class is very much like plist in the sense it stores key-value pairs.

It is not recommended storing anything with sensitive user information (username, password, etc) as these values are saved in a plain text .plist file in the documents directory.

To read from or write to NSUserDefaults, one has to get a reference to it.  In the simplest use of NSUserDefaults, this is done via a method that returns a reference to an object capable of interacting with NSUserDefaults's data store.

### Q16: How to make IOS libraries in accessible in Xamarin apps?
Xamarin.iOS supports linking with both native C libraries and Objective-C libraries.

For linking with third-party C libraries, it is required that all the libraries be linked statically.

Following are the steps one needs to follow to consume third party C Libraries:

Bring the Library into your project: Select your project from the Solution Explorer and locate the file on your disk and add it to the project. When prompted, tell Visual Studio for Mac or Visual Studio to copy it into the project. After adding it, find the library in the project, right-click on it, and set the Build Action to none.
Configure Xamarin.iOS to link the library: Now on the project options of your project,  add in iOS Build's extra argument, the "-gcc_flags" option followed by a quoted string that contains all the third-party libraries that are required for your project
Access the methods from the library: For this,  use Mono's Platform Invoke (P/Invoke) to access these methods from C#.

### Q17: What are services in Xamarin.android?
A Service is an application component that allows a user to run long operations that do not require user interaction. Services are broadly classified into Started and Bound Service.

A Started service is one which is invoked by call StartService(). Once started the service can run indefinitely in the background, even after the component that started it is destroyed. Usually, a started service performs a specific operation (like downloading a file) and stops itself. A  User-defined Started Service can be created by either extending the Service class or by extending the Intent Service. An Intent Service is a special type of Service which stops itself automatically after completing the task assigned.

A Bound Service is created when the application component calls BindService() to bind to a service. Bound Service is like a Client-server interface that allows components to interact with the service, send requests, get results, etc. A Bound service can be accessed by the components within an application and also by components residing in other applications (if it is exported/exposed). Bound Services only keep running till they have a client associated with it. When all clients Unbind the service the service stops

### Q18: What is AsyncTask in Xamarin.Andriod?
AsyncTask is a facility given by Android for executing operations in a background thread without having to manually handle thread creation or execution

Aynctask has following important callback methods:

OnPreExecute:  OnPreExecute is invoked before the actual Background Task is executed. It is used to initialize the Asynctask or setup the task  For example setting up the progress bar to show while the task is being executed
DoInBackground(Params … params): This is the main call back function which contains the code to do the background operation which may take a long time. The parameters of Asynctask are passed to this step and doInBackground can utilize them
OnProgressUpdate: On Progress Update is a method which is called repeatedly and can be used to publish the progress that has been made by the background tasks so far
OnPostExecute (Result result). : This is invoked on the UI thread. When the task is completed in DoInBackground the result is returned to this call-back. The user can display the result or store for an app to process.
Asynctasks should always be created and loaded on the GUI thread. They cannot be started more than once.
### Q19: What is pendingintent in Xamarin.Android?

A Pending Intent wraps another intent object. A Pending Intent means the intent that is being enclosed may not be executed now but some time in the future. Pending Intent can be passed on to a foreign application thereby granting that app the right to perform the operation represented by the intent

A PendingIntent itself is a token referencing the original content of the intent viz the action, data, categories, etc. Even if the owning app is killed by the system, PendingIntent can still be executed and it will again bring back the app back in memory. An app after providing the PendingIntent to a foreign app can cancel the need be. PendingIntent can be created for an Activity(through GetActivity() or Broadcast ( via GetBroadcast Method or service (via GetService() method).

### Q20: What are provisioning profiles in Xamarin.IOS?
Ans:
Unlike Android, iOS does not allow users to directly install third-party apps. Only those apps that are signed by Apple can only be installed by the iOS users. The provisioning profile is a link between the Developer of the app (his Developer Account) and the Device on which it is being used. The provisioning profile is downloaded from the developer account and the entire bundle is code-signed by the iOS. A Development Provisioning Profile must be installed on each device on which the developer wishes to run his application. If the information in the provisioning profile doesn't match certain criteria, the app won't launch.

A provisioning profile necessarily consists of:

Development Certificates : These are for developers who want to test the app on a physical device while writing code
Unique Device Identifiers:  the List of devices that the app can run on
An App ID: It is a two-part string used to uniquely identify different apps from a single development team.

### Q21:What are the different types of gestures supported by Xamarin.Forms?
Mobile gestures are the movements made by a user to perform a specific action on a control within a mobile interface majorly through fingers(tap, swipe, drag, slide, etc.). The various Gestures supported by Xamarin.Forms are:

Tap Gesture: Xamarin supports the tap gesture. A tap gesture is recognised when the user touches the mobile screen with single or multiple fingers once or twice in quick succession. The Tap Gesture is recognized with TapGestureRecognizer Class class.
Pinch  Gesture: Pinch Gesture occurs when the user places two fingers on the screen at a distance and brings them towards each other or keeps them together and moves them away from each other. This gesture is common to zoom in or out in a map mode. The Pinch Gesture is recognized with PinchGestureRecognizer Class.
Pan Gesture: A pan gesture is used for detecting the movement of fingers around the screen. These movements are then applied to the content currently at the display. It is recognized with  the PanGestureRecognizer class
Swipe Gesture: A swipe gesture occurs when a finger is moved across the mobile screen in a horizontal or vertical direction and is often used to initiate navigation through content. Swipe gestures are recognized with SwipeGestureRecognizer class.

### Q22: Performance Improvements in Xamarin.Forms?
Ans:
##### Enable th XAML Compiler
XAML can be optionally compiled directly into intermediate language (IL) with the XAML compiler (XAMLC). XAMLC offers a number of benefits:

It performs compile-time checking of XAML, notifying the user of any errors.
It removes some of the load and instantiation time for XAML elements.
It helps to reduce the file size of the final assembly by no longer including .xaml files.
XAMLC is enabled by default in new Xamarin.Forms solutions. However, it may need to be enabled in older solutions. 

##### Use compiled bindings
Compiled bindings improve data binding performance in Xamarin.Forms applications by resolving binding expressions at compile time, rather than at runtime with reflection. Compiling a binding expression generates compiled code that typically resolves a binding 8-20 times quicker than using a classic binding.

##### Reduce unnecessary bindings
Don't use bindings for content that can easily be set statically. There is no advantage in binding data that doesn't need to be bound, because bindings aren't cost efficient. For example, setting Button.Text = "Accept" has less overhead than binding Button.Text to a viewmodel string property with value "Accept".

##### Use Fast Renderers
Fast renderers reduce the inflation and rendering costs of Xamarin.Forms controls on Android by flattening the resulting native controls hierarchy. This further improves performance by creating fewer objects, which in turn results in a less complex visual tree and less memory usage.

##### Enable layout compression
Layout compression removes specified layouts from the visual tree, in an attempt to improve page rendering performance. The performance benefit that this delivers varies depending on the complexity of a page, the version of the operating system being used, and the device on which the application is running. However, the biggest performance gains will be seen on older devices. 

##### Choose the correct layout 

##### Optimize layout performance
To obtain the best possible layout performance, follow these guidelines:

Reduce the depth of layout hierarchies by specifying Margin property values, allowing the creation of layouts with fewer wrapping views. For more information, see Margins and Padding.
When using a Grid, try to ensure that as few rows and columns as possible are set to Auto size. Each auto-sized row or column will cause the layout engine to perform additional layout calculations. Instead, use fixed size rows and columns if possible. Alternatively, set rows and columns to occupy a proportional amount of space with the GridUnitType.Star enumeration value, provided that the parent tree follows these layout guidelines.
Don't set the VerticalOptions and HorizontalOptions properties of a layout unless required. The default values of LayoutOptions.Fill and LayoutOptions.FillAndExpand allow for the best layout optimization. Changing these properties has a cost and consumes memory, even when setting them to the default values.
Avoid using a RelativeLayout whenever possible. It will result in the CPU having to perform significantly more work.
When using an AbsoluteLayout, avoid using the AbsoluteLayout.AutoSize property whenever possible.
When using a StackLayout, ensure that only one child is set to LayoutOptions.Expands. This property ensures that the specified child will occupy the largest space that the StackLayout can give to it, and it is wasteful to perform these calculations more than once.
Avoid calling any of the methods of the Layout class, as they result in expensive layout calculations being performed. Instead, it's likely that the desired layout behavior can be obtained by setting the TranslationX and TranslationY properties. Alternatively, subclass the Layout<View> class to achieve the desired layout behavior.
Don't update any Label instances more frequently than required, as the change of size of the label can result in the entire screen layout being re-calculated.
Don't set the Label.VerticalTextAlignment property unless required.
Set the LineBreakMode of any Label instances to NoWrap whenever possible.
  
  
##### Use asynchronous programming
##### Use CollectionView instead of ListView
##### Use the custom renderer pattern
### Q22: What is Xamarin Profiler?
Ans:
Xamarin Profiler is a tool which is used by the developers to keep an eye on the information about the particular App inside the Visual Studio. With the help of Xamarin Profiler, developers can easily analyze the App's behavior. We can use the profiler to track the application's memory information and can sample its statistics.

https://docs.microsoft.com/en-us/xamarin/xamarin-forms/app-fundamentals/custom-renderer/entry



