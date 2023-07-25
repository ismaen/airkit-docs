Airkit provides the ability to take a selected appointment window from a [Scheduler Web Control](https://support.airkit.com/reference/scheduler-web-control) and pass that to an external scheduling system. This section will cover the following:


1. [Capturing the selected time slot](#h_01F222W8FD0P4VTM48ZRQ9HQ2F)
2. [Create a Google Calendar Event from the scheduler control](#h_01F1NQYQKQ9X70612NH96283KS)
3. [Create an .ics file](#h_01F1NWYP4TX104AAJFKXN3K1KN)


Capturing the selected time slot
--------------------------------


To capture a selected appointment window from Scheduler Web Control, the selected time (in the form of a DateTime) has to be passed to a variable. From there, the selected [DateTime](https://support.airkit.com/reference/the-datetime-variable-data-type) can be used throughout a [Journey](https://support.airkit.com/docs/journeys). This section will go over how to capture the selected appointment time to a variable. 


1. Create a [DateTime variable](https://support.airkit.com/reference/the-datetime-variable-data-type) on the Web Page by selecting your [Web Page](https://support.airkit.com/docs/web-flows) and in the Inspector and add a variable. Set the variable name to “time_slot”.  
![timeslot.png](./assets_v1714/integrating-to-external-calendar-systems-v1714-0.png)
2. Select the scheduler control and click on **Actions** in the inspector. Then add the [Set Variable action](https://support.airkit.com/reference/the-set-variable-action) on value change. This is where the outputs of the scheduler control is bound to the variable. The example below shows the start time of the selected value being stored to **time_slot**.   
![actions_slot.png](./assets_v1714/integrating-to-external-calendar-systems-v1714-1.png)  
  
The outputs of the selected time slot can be retrieved through:

```javascript Airscript
event.value
```

Event.value will contain a [Schedule Object](https://support.airkit.com/docs/schedule-objects). A sample output of event.value is:

```json Airscript
{  
"start_time":{  
  "date":{  
    "year":2021,  
    "month":3,  
    "day":30  
  },  
  "time":{  
    "hour":20,  
    "minute":0,  
    "second":0,  
    "millisecond":0  
  },  
  "timeZone":"UTC"  
},  
"end_time":{  
  "date":{  
    "year":2021,  
    "month":3,  
    "day":30  
  },  
  "time":{  
    "hour":21,  
    "minute":0,  
    "second":0,  
    "millisecond":0  
  },  
  "timeZone":"UTC"  
},  
"calendar_event_id":"",  
"calendar_id":"",  
"recurrence":364  
}
```


Create a Google Calendar event from the scheduler control
---------------------------------------------------------


This guide will walk through the steps on how to take the selected DateTime and insert that as an event to a Google calendar. 


Pre-requisites:


* Set up application for [Google Calendar API](https://developers.google.com/calendar/auth)
* Configure [Google integration within Airkit](https://support.airkit.com/docs/setting-up-integrations)


After configuring the Google integration in the application, the next step is to add a [Data Flow](https://support.airkit.com/docs/data-flows) to receive inputs of the selected event start time and event end time, and then send an [HTTP request](https://support.airkit.com/reference/http-request-data-operation) to write back to a Google Calendar. 


1. Add a Data Flow that takes two [text](https://support.airkit.com/reference/the-text-variable-data-type) inputs: **start_time** and **end_time**. (**Note**: The outputs of the scheduler web control are [DateTime objects](https://support.airkit.com/docs/working-with-date,-time-and-datetime-in-airscript), but this example will be formatting the DateTime objects to [RFC3339](https://tools.ietf.org/html/rfc3339) before passing it to the Data Flow.)  
  
![googleintegration.png](./assets_v1714/integrating-to-external-calendar-systems-v1714-2.png)
2. Add a HTTP request data operation and select the Google service created in the pre requisite step. Change the method to POST and change the URL to:  


```
[https://www.googleapis.com/calendar/v3/calendars/{{calendarID}}/events](https://www.googleapis.com/calendar/v3/calendars/iaboubakare@gmail.com/events)
```

  
![googlehttp.png](./assets_v1714/integrating-to-external-calendar-systems-v1714-3.png)
3. Add the request body to the HTTP Request. This example will insert an event with the start time and end time from the scheduler control and with a Title of "Scheduled Event". For more information on the Google Calendar Events api, see [here](https://developers.google.com/calendar/v3/reference/events/insert).   
  



```javascript Airscript
{  
"end":  
{ "dateTime": end_time, "timeZone": "America/Chicago" },  
"start":  
{ "dateTime": start_time, "timeZone": "America/Chicago" },  
"summary": "Scheduled Event"  
}
```
4. Now that the Data Flow is completed, the start time and end time of a selected time slot can now be passed as an input to the Data Flow. Add a Data Flow by clicking on the '+' icon under Actions in the inspector of the scheduler control.   
![schedulerdataop.png](https://a01-support.airkit.com/integrating-to-external-calendar-systems/schedulerdataop.png)
5. Then select the Data Flow previously created. This will expect two inputs: start_time and end_time. In the inputs, provide the following:  
  
**start_time:**  



```javascript Airscript
FORMAT_DATETIME(event.value.start_time)
```


  
**end_time:**  



```javascript Airscript
FORMAT_DATETIME(event.value.end_time)
```


  
The [Format_DateTime](https://support.airkit.com/reference/format_datetime) function provides the ability to format the datetime object to [RFC3339](https://tools.ietf.org/html/rfc3339) format so that the Google Calendar API can read it.


Create an .ics file
-------------------


Creating an .ics file is useful in situations where a journey requires the ability download and import event details into a calendar. This section will walk through creating a downloadable .ics file that contains the content of the selected time slot using the scheduler control and Data Flows. 


1. After adding a scheduler control to the webpage and configuring the calendars, add a Data Flow with two text inputs: start_time and end_time. (**Note**: The outputs of the scheduler web control are [DateTime objects](https://support.airkit.com/docs/working-with-date,-time-and-datetime-in-airscript), but this example will be formatting the DateTime objects to [RFC3339](https://tools.ietf.org/html/rfc3339) before passing it to the Data Flow.)  
![ics_startend.png](https://a01-support.airkit.com/integrating-to-external-calendar-systems/ics_startend.png)
2. Add a [Create File](https://support.airkit.com/reference/the-create-file-data-operation) data operation and configure the following properties:  
**Filename**: "invite.ics"  
**Content**:   



```
"BEGIN:VCALENDAR  
VERSION:2.0  
BEGIN:VEVENT  
CLASS:PUBLIC  
DESCRIPTION:Check out this event!  
DTSTART:{{start_time}}  
DTEND:{{end_time}}  
LOCATION:Home  
SUMMARY;LANGUAGE=en-us:Scheduled Time  
END:VEVENT  
END:VCALENDAR"
```


**Scope:** App **Visibility:** Private**Download Url Expiration**: 1 Hour  
The content that is being passed is merely a template and can be edited and modified. For more information on .ics extension type, check out [iCalendar.org](https://icalendar.org/). Also, {{start_time}} and {{end_time}} are the input variables passed as a string. For more information on this syntax, check out [The Text Variable Data Type](https://support.airkit.com/reference/the-text-variable-data-type).
3. Pass the **file variable** as the return value so that it can be bound to a variable within the application.   
![assetoutput.png](https://a01-support.airkit.com/integrating-to-external-calendar-systems/assetoutput.png)
4. Go back to [App Builder](https://support.airkit.com/docs/web-builder) and create a web page text variable and call it **download_ics.**This is going to be used to store the outputs of the Data Flow.   
![downloadics.png](https://a01-support.airkit.com/integrating-to-external-calendar-systems/downloadics.png)
5. Add a Data Flow by clicking on the '+' icon under Actions in the inspector of the scheduler control.   
![rundataop_ics.png](https://a01-support.airkit.com/integrating-to-external-calendar-systems/rundataop_ics.png)
6. Then select the Data Flow previously created. This will expect two inputs: start_time and end_time. In the inputs, provide the following:  
  
**start_time:**  



```javascript Airscript
FORMAT_DATETIME(event.value.start_time)
```


  
**end_time:**  



```javascript Airscript
FORMAT_DATETIME(event.value.end_time)
```


  
For the Output Binding:

```javascript Airscript
download_ics
```

The [Format_DateTime](https://support.airkit.com/reference/format_datetime) function provides the ability to format the datetime object to [RFC3339](https://tools.ietf.org/html/rfc3339) format so that the it is properly formatted for the .ics file.
7. Once the Data Flow is configured, add a [Hyperlink control](https://support.airkit.com/reference/hyperlink-web-control) to the webpage to provide a place to trigger the download. On the href property of the Hyperlink control, enter **download_ics.downloadUrl**, which will pass the download url as the reference link, and change the Text property to "Download .ics file". Now the HyperLink control will download the .ics file of the selected time slot when clicked!  
![download_icsdownloadurl.png](./assets_v1714/integrating-to-external-calendar-systems-v1714-4.png)


Further Reading
---------------


For additional reference and information, below are some additional topics to dive deeper and may be useful when leveraging scheduling capabilities within Airkit.


* [Calendar Based Scheduling](https://support.airkit.com/docs/using-the-scheduler-web-control-to-reschedule-deflected-calls)
* [Journey Specific Timers & Reminders](https://support.airkit.com/docs/journey-specific-timers-and-reminders)
* [Calendar Builder](https://support.airkit.com/docs/calendar-builder)
* [How To enforce TCPA](https://support.airkit.com/docs/how-to-enforce-tcpa)
* [Working with Date, Time & DateTime in Airscript](https://support.airkit.com/docs/working-with-date,-time-and-datetime-in-airscript)