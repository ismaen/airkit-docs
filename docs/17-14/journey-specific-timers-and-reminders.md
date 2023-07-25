The [Timer](https://support.airkit.com/reference/the-create-timer-action) action can be used to run actions at designated times. Timers have the capability to run at a specified time and also have options to be [TCPA](https://support.airkit.com/docs/tcpa) compliant as well.  For example, a Timer can be set to send a reminder to a customer 5 minutes before their selected call time.   

<img src="./assets_v1714/journey-specific-timers-and-reminders-v1714-0.png" alt="organizing info" style="max-width: 300px; width:100%;"/>


But sometimes, that reminder may be set to send outside of TCPA compliant hours. In order to comply by TCPA restrictions, Timers have the option to pass in a TCPA compliant [Availability Schedules](https://support.airkit.com/docs/calendar-builder) from the customer's timezone and send the reminder in the previous/upcoming available window.   

<img src="./assets_v1714/journey-specific-timers-and-reminders-v1714-1.png" alt="organizing info" style="max-width: 300px; width:100%;"/>


### Best Practices using Timers


* When using Timers for customer reminders, it is always good practice to comply by TCPA restrictions. Check out [How to enforce TCPA](https://support.airkit.com/docs/how-to-enforce-tcpa) for more information.
* Timer Keys are required to be unique across the application when creating timers.
* It is good practice to use the [Cancel Timer action](https://support.airkit.com/reference/the-cancel-timer-action) when the Timer is no longer needed in the customer journey. Don't rely on session management to cancel the timers.
* Build out Timers that are tied to events. This enables you to have full control over the inputs and management of your Timers.
* Timers only have access to data that is tied to the client state. If a Timer is created on an event, data cannot be passed from the event namespace to an action in the timer. If passing data from the event namespace, data must be stored in a temporary variable and then pass the temporary variable to the actions associated with the timer.


### Augmenting Timers based on Availability Schedules


Like mentioned above, Timers have the ability to run based off of a specified [Availability Schedule.](https://support.airkit.com/docs/calendar-builder) This section will walk through how to set up a timer to execute 5 minutes before a selected appointment time and comply with TCPA restrictions. 


1. Create a timer in the Action tab of the control. This example will be adding it to the value changed of the [Scheduler Web Control](https://support.airkit.com/reference/scheduler-web-control), but Timers can be created in many other events as well.   

<img src="./assets_v1714/journey-specific-timers-and-reminders-v1714-2.gif" alt="organizing info" style="max-width: 350px; width:100%;"/>


2. In the Create Timer configuration, you can either specify a time or add a custom expression. To schedule a Timer to run based off the selected time slot, a [DateTime](https://support.airkit.com/reference/the-datetime-variable-data-type) has to be passed in as a custom expression and then modified using the [SUBTRACT_FROM_DATETIME](https://support.airkit.com/reference/subtract_from_datetime) function. In the Custom Expression, enter the following Airscript expression:  


```javascript Airscript
SUBTRACT_FROM_DATETIME(event.value.start_time, 5, "m")
```

This will pass the start_time and subtract 5 minutes. The output of the time will be the time that the timer executes.    

<img src="./assets_v1714/journey-specific-timers-and-reminders-v1714-3.png" alt="organizing info" style="max-width: 300px; width:100%;"/>


3. Once the execution time is defined, then determine if the Timer requires any restrictions to be TCPA compliant.  Select a calendar and choose what action to take if the time is not available or within the calendar window. You can choose from the following:  

	* Don't Schedule and cancel
	* Use next available time
	* Run in previous available window
	* Schedule anyway  
	  

<img src="./assets_v1714/journey-specific-timers-and-reminders-v1714-4.png" alt="organizing info" style="max-width: 300px; width:100%;"/>