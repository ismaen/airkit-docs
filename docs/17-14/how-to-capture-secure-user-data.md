Introduction
------------


Some data is just too precious to leave a trace behind. At Airkit, we understand that the security of customer data is important. This article will explore how to use *Secure Strings* within the Airkit platform.


*Secure Strings* provide you a way to capture sensitive information from the user. This might be the individual's password, their driver's license number, or maybe Social Security Number. This particular kind of information is some of the most sensitive information you can collect about a user and requires an extra level of care.


Security Details
----------------


Data stored with the Secure String Input control cannot be accessed by the client, and can only be accessed via the Secure Value Retrieval frame operation. Each keystroke by the user is encrypted and transmitted over the network and back to our secure store, where the data is separated from the rest of the users data. This data is only stored for *30 minutes*, so it’s important that you process or use this data in a timely fashion. After that allotted time, we scrub the data from our systems entirely.


Securely Capturing Data Using Secure String Input Control
---------------------------------------------------------


Secure String Input is one of the Form controls that you can add to the Canvas. Navigate to your card view or container, and click on the **+** button to add this control to your page.


![image-1.png](./assets_v1714/how-to-capture-secure-user-data-v1714-0.png)


Unlike normal String Inputs, you have to manually configure the variable you’d like the data to be saved to. After adding the control, navigate to the Actions tab in the inspector. Add a set-variable action to the **Value Changed** event. Enter the variable name, and for the value enter **event.value**.


Configuring this event will now ensure that as your users enter data into the control that it’s saved securely.


![image-2.png](./assets_v1714/how-to-capture-secure-user-data-v1714-1.png)


Finally, we’ll configure the masking options on the control. Go back to the General tab of the Secure Input Control, and find the icon options. By adding a password-visibility to either the left or right icon, you can now hide the input as the user is typing. This provides an additional layer of security to mask the users keystrokes as they are typing.


Retrieving the Secure Data
--------------------------


Once your data is safely secured, you can extract it using a Data Operation. We’ll start by going to Connection Builder and creating a new Data Operation. Create an input for your Data Operation called **secure_value_key**. Add a Frame and select *Secure Value Retrieval* as the frame operation. Provide the **secure_value_key** variable to this Frame.


The **Secure Value Retrieval** is a frame operation which retrieves your data from our secure store. This frame operation returns a variable with the original user input.


![image-3.png](./assets_v1714/how-to-capture-secure-user-data-v1714-2.png)


The output variable can be used in subsequent frame operations or it can be returned to the main application. If you return the secure value from the Data Operation, the value will no longer be secure.


Using the Secure Data Operation
-------------------------------


The retrieval operation data operation can be invoked anywhere an action can. A typical approach would invoke this data operation as part of a Submit button’s **onClick** event.


To start, lets look at the data that comes out of the input control:



```javascript Airscript
{
  "redisKey": "SecureStringInput-398dcf5c-115c-4994-aa65-1192ddf92f0f",
  "success": true
}

```

This contains 2 values, a **redisKey** and a **success** field. The **redisKey** is the key that you'll use to retrieve your secure value. The **success** value shows you if the data was successfully stored.


To configure the Data Operation, pass the **redisKey** in as the input to the Data Operation. This will go into the **secure_value_key** input variable. The **secure_value_key** will be the input into your **Secure Value Retrieval** frame operation, thus allowing you to retrieve the data for the specified key.


![image-4.png](./assets_v1714/how-to-capture-secure-user-data-v1714-3.png)


After configuring the action, you now can test the entire flow inside the debugger.


Conclusion
----------


Using the Secure String Input in conjunction with the Secure Value Retrieval frame operation creates an end-to-end secure flow. You can safely retrieve the information within a data operation, and then utilize that information with subsequent frames within your data operation. This security model allows you to be certain that Airkit can capture secure information about your users without storing that information long term.