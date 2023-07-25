This article will go over how to use the [Scheduler Web Control](https://support.airkit.com/reference/scheduler-web-control) to reschedule deflected calls as well as how to change the behavior of an application based on operating hours.


Smoothing demand with scheduled callbacks
-----------------------------------------


Increased demand to get a human agent on a call with a customer can result in long wait times when there aren't enough agents to field the demand that is coming in. One way to remediate this is through call deflection and enabling your customer to schedule a time to have the agent call back. 


The [Scheduler Web Control](https://support.airkit.com/reference/scheduler-web-control) allows users to select from a list of dates and times, and also control what dates and times are made available through the [Calendar Builder](https://support.airkit.com/docs/calendar-builder).


![mceclip1.png](./assets_v1714/using-the-scheduler-web-control-to-reschedule-deflected-calls-v1714-0.png)


 


One method of smoothing demand with scheduled callback is through call deflection to SMS. The [Journey](https://support.airkit.com/docs/journeys) would look something like this:


1. Customer makes an inbound call and IVR asks if customer would like to stay on hold or schedule a time to call back.
2. Customer chooses to schedule a time to call back
3. Customer receives an SMS message with a link to an application to schedule their callback time


The application that is sent to the customer includes the Scheduler Web Control, which allows the customer to select an appointment slot to be called back at. Below are steps to integrate the scheduler web control within an application.


### Adding the Scheduler Web Control and connecting to an Availability Schedule


1. Add the [Scheduler Web Control](https://support.airkit.com/reference/scheduler-web-control) to the web page by clicking on '+' next to the web page.   

[block:image]
{
  "images": [
    {
      "image": [
        "./assets_v1714/using-the-scheduler-web-control-to-reschedule-deflected-calls-v1714-1.png",
        "mceclip1-scheduler.png",
        666,
        619,
        "#f4f2f3"
      ]
    }
  ]
}
[/block]
2. Once the scheduler is added to the Stage, you can configure the control properties as well as the scheduler properties.  To connect an Availability Schedule to the Scheduler Web Control, go to the Inspector and select an Availability Schedule from the dropdown list. The Availability Schedule selected will determine what time slots show up to the end user. (For more on what Availability Schedules are and how to create one that serves specific needs, check out documentation on [Calendar Builder](https://support.airkit.com/docs/calendar-builder-Calendar-Builder).)  
![mceclip0.png](./assets_v1714/using-the-scheduler-web-control-to-reschedule-deflected-calls-v1714-2.png)


### Creating Schedule Object


In order to write back information pertaining to the selected appointment block, create a Schedule Object in [AirData](https://support.airkit.com/docs/working-with-data) to store it. Within AirData there is a built in [Schedule Object](https://support.airkit.com/docs/schedule-objects) that can be created without much configuration. 


1. To add a Schedule Object to AirData, go to [Data Builder](https://support.airkit.com/docs/data-builder), click on the '+' icon, and select Add Schedule. This will create a predefined Schedule Object that you can associate with your scheduler. You are also able to add additional properties as well.   
![2021-03-23_11-07-35__2_.gif](./assets_v1714/using-the-scheduler-web-control-to-reschedule-deflected-calls-v1714-3).gif)
2. Rename the Schedule Object and Save. This example will use the name 'CustomerSchedule'.  
![mceclip3.png](./assets_v1714/using-the-scheduler-web-control-to-reschedule-deflected-calls-v1714-4.png)


### Writing to the Schedule Object


Once the [Schedule Object](https://support.airkit.com/docs/schedule-objects) is configured, it can be used to store a user's selection from the Scheduler Web Control. To write back the selection to AirData, the scheduler control needs to be connected to the Schedule Object.


1. Return to the [Web Builder](https://support.airkit.com/docs/web-builder) and select the Scheduler Web Control in the Tree. In the Inspector, configure the scheduler to the Schedule Object you created.  
![mceclip1.png](./assets_v1714/using-the-scheduler-web-control-to-reschedule-deflected-calls-v1714-5).png)  
Once configured, the scheduler will automatically write to the [Schedule Object](https://support.airkit.com/docs/schedule-objects) whenever an appointment block is selected.


### Changing behavior based on operating hours


There are a few different approaches to restrict the ability to send/receive calls or texts outside of operating hours. The first approach is to enforce [TCPA](https://support.airkit.com/docs/tcpa) restrictions through the use of restrictions on Availability Schedules and Timers. For more information on TCPA, see [How to enforce TCPA](https://support.airkit.com/docs/how-to-enforce-tcpa). 


Another approach is through the use of the [Calendar Search](https://support.airkit.com/reference/the-calendar-search-data-operation) Data Operation. The Calendar Search Data Operation has the ability to check and see if there are currently any appointment times available in the current time, in the previous time window, or in the upcoming time window. The video below will walk through the scenario of building out an experience where if the user is checking the application at a given time, and will give them the option to schedule an appointment (if user is not within operating hours) or give them the option to call (if user is within operating hours).   
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FS4PmZLO7fME%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DS4PmZLO7fME&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FS4PmZLO7fME%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=S4PmZLO7fME",
  "title": "Calendar Search",
  "favicon": "https://www.youtube.com/s/desktop/15c06292/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/S4PmZLO7fME/hqdefault.jpg"
}
[/block]
Further Reading
---------------


For additional reference and information on calendar based scheduling, below are some additional topics to dive deeper and may be useful.


* [Integrating to External Calendar Systems](https://support.airkit.com/docs/integrating-to-external-calendar-systems)
* [Journey Specific Timers & Reminders](https://support.airkit.com/docs/journey-specific-timers-and-reminders)
* [How To enforce TCPA](https://support.airkit.com/docs/how-to-enforce-tcpa)
* [Working with Date, Time & DateTime in Airscript](https://support.airkit.com/docs/working-with-date,-time-and-datetime-in-airscript)