## What is Intent?🙄
Intent is a message that allows one application component to interact with another component. In other words, an Intent is an object used to start an operation or send a data set to another component.

Intents are primarily used to facilitate interaction between Android applications. For example, a user may need another application to send an email from their email application. In this case, the email application can create an Intent and add the email data they want to send to this Intent. Afterwards, this Intent is processed by another application and the email sending operation is performed.

### Types of Intents ✌️
There are two different types of Intents in Android: explicit and implicit Intents.

### 1. Explicit Intents
Explicit Intents explicitly specify the target component (activity, service, etc.). This type of Intent contains information that specifies a specific target, such as the name of a component or the package name and name of a component.

For example, in the following code snippet, an Explicit Intent instance is created from the MainActivity class to the MyOtherActivity class:
````
val intent = Intent(this, MyOtherActivity::class.java)
startActivity(intent)
````
This code creates an Intent to switch from MainActivity to MyOtherActivity and starts this Intent with the startActivity() method.

### 2. Implicit Intents
Implicit Intents are typically used to interact with an application or component selected by the user to perform an action. For example, when a user selects a gallery application to view a photo, this selection is given to an Implicit Intent and the appropriate application is launched. For example, opening a web page with an Implicit Intent:
````
val intent = Intent("https://www.aliosmanarslan.com/")
intent.data = Uri.parse(getWebSite.toString())
startActivity(intent)
````
The following code example demonstrates opening the gallery application to select an image using an Implicit Intent:
````
val intent = Intent(Intent.ACTION_PICK, MediaStore.Images.Media.EXTERNAL_CONTENT_URI)
startActivityForResult(intent, PICK_IMAGE_REQUEST)
This code snippet creates an implicit Intent example to pick an image from the MediaStore.Images.Media.EXTERNAL_CONTENT_URI database using the ACTION_PICK action and starts it with the startActivityForResult() method.
````
## Using Intents🤔
Intents are often used to open another component, such as an activity or service, to perform an action or send a data set.

### 1. Opening Another Component
Using an Intent, another component (activity, service, etc.) can be opened. The following code snippet creates an Explicit Intent example to switch from the MainActivity class to the MyOtherActivity class and starts it with the startActivity() method:
```
val intent = Intent(this, MyOtherActivity::class.java)
startActivity(intent)
````
### 2. Performing an Action
An action can be performed using an Intent. For example, the following code creates an Implicit Intent instance to start a phone call:
````
val intent = Intent(Intent.ACTION_CALL, Uri.parse("tel:" + phoneNumber))
startActivity(intent)
````
### 3. Sending a Data Set
Using an Intent, a data set can be sent to another component. The following code snippet creates an Explicit Intent instance to send a string data set from the MainActivity class to the MyOtherActivity class:
````
val intent = Intent(this, MyOtherActivity::class.java)
intent.putExtra("myData", "Hello World!")
startActivity(intent)
````
This code snippet sends a string data with the key “myData” to the MyOtherActivity component.

### 4. Opening Camera Application
When you want to use the camera in an application, you can use an implicit intent to open the camera application. For example:
````
val intent = Intent(MediaStore.ACTION_IMAGE_CAPTURE)
startActivity(intent)
````
This code snippet creates an implicit intent example using the MediaStore.ACTION_IMAGE_CAPTURE action to open the camera application and starts it with the startActivity() method.

### 5. Making a Phone Call
You can use an implicit intent to make a phone call with a specific phone number. For example:
````
val phoneNumber = "1234567890"
val intent = Intent(Intent.ACTION_DIAL, Uri.parse("tel:$phoneNumber"))
startActivity(intent)
````
This code snippet creates an implicit intent example using the ACTION_DIAL action to make a phone call and starts it with the startActivity() method.
### 6. Opening a Web Page
You can use an implicit intent to open a web page. For example:
````
val webPage = "https://www.aliosmanarslan.com"
val intent = Intent(Intent.ACTION_VIEW, Uri.parse(webPage))
startActivity(intent)
````
This code snippet creates an implicit intent instance using ACTION_VIEW action to open a web page and starts it with the startActivity() method.

### 7. Receiving Data
You can use an explicit intent to receive data from another application. For example:
````
val intent = Intent(Intent.ACTION_GET_CONTENT)
intent.type = "image/*"
startActivityForResult(intent, PICK_IMAGE_REQUEST)
````
This code snippet creates an explicit intent example using ACTION_GET_CONTENT action to select an image from another application, and starts it using the startActivityForResult() method. The selected data is returned through the onActivityResult() method.

## Intent with Service
A Service is a component used to execute a background process. By using Intents, you can start and stop a Service. For example, in a media player application, you can use a Service to play a song. Below is an example code snippet on how to use Intents with Services:
````
// Create an Intent to start the Service
val intent = Intent(this, MyService::class.java)
startService(intent)

// Create an Intent to stop the Service
val intent = Intent(this, MyService::class.java)
stopService(intent)
````
This code snippet demonstrates examples of using Intent to start or stop a Service. You can replace the “MyService” with the name of your own Service class in your application.
## Using Intent with Broadcast
A broadcast is a message that is broadcasted within or outside of an application. You can use Intents to start a BroadcastReceiver component and listen for a broadcasted message. For example, in an alarm application, you can use a Broadcast to trigger an alarm. Below is an example code snippet that shows how to use Intent with Broadcast operations:
````
// Create an Intent to send a Broadcast
val intent = Intent("com.example.myapp.MY_ACTION")
sendBroadcast(intent)

// Create a BroadcastReceiver component to receive a broadcast.
class MyReceiver : BroadcastReceiver() {
    override fun onReceive(context: Context, intent: Intent) {
        if (intent.action == "com.example.myapp.MY_ACTION") {
            // Handle the broadcast message
        }
    }
}

// Register the BroadcastReceiver component.
val receiver = MyReceiver()
val filter = IntentFilter("com.example.myapp.MY_ACTION")
registerReceiver(receiver, filter)

// Unregister the BroadcastReceiver component.
unregisterReceiver(receiver)
````
This code snippet demonstrates examples of using Intent to send and receive a Broadcast. You can use your own Broadcast message name instead of “com.example.myapp.MY_ACTION” in your application. Additionally, you can use the registerReceiver() and unregisterReceiver() methods to register and unregister the BroadcastReceiver component.



