The Calendar Builder provides the tools to create **Availability Schedules**. These can be referenced by the [Scheduler Web Control](https://support.airkit.com/reference/scheduler-web-control) to define the windows of time in which the Scheduler can be used to make appointments. The Availability Schedules are made by combining **Time Slots**, which are themselves also defined in the Calendar Builder.


Changes made in the Calendar Builder differ from changes made in most other Builders in that they do not only effect the app being immediately edited, they will be applied to all apps stored in their [Organization](https://support.airkit.com/docs/airkit-organizations). Take particular care when using the Calendar Builder to edit existing Availability Schedules or Time Slots, as the app being edited might not be the only one impacted by your changes.


Like most Builders, the layout of the Calendar Builder maps comfortably onto the general structure of the Studio: to the immediate right of the Builder Bar is the Tree, to the right of which is the Stage, to the right of which is the Inspector: 


![Calendar_Builder_Layout.png](./assets_v1714/calendar-builder-v1714-0.png)



# Tree


The Tree is where you'll find an expandable and collapsible breakdown of Availability Schedules and Time Slots. Branching of this Tree consists of:


* Availability Schedules
  * All available Availability Schedules, both custom and pre-made
* Time Slots
  * All available Time Slots, both custom and pre-made


New Availability Schedules or Time Slots can be added in the same way: by clicking on the '+' icon to the right of the relevant branch in the Tree. Likewise, both Availability Schedules and Time Slots can be deleted by clicking the trash icon to their immediate right:


![2021-09-23_14-56-48__1_.gif](./assets_v1714/calendar-builder-v1714-1).gif)


## Availability Schedules


Availability Schedules define the windows in which appointments can be scheduled. They are made by combining the requirements of arbitrarily many Time Slots, see below.


Out of the box, Airkit comes with several Availability Schedules (as well as their component Time Slots) pre-configured. These correspond to regional [TCPA regulations](https://support.airkit.com/docs/tcpa); utilizing them streamlines the process of creating TCPA-compliant apps.


## Time Slots


Time Slots define simple patterns of one-off or reoccurring blocks of time. A Time Slot might be, for instance, *every day from 8AM to 9PM PST*.


Time Slots are the component parts of Availability Schedules, and the blocks of time they describe are necessarily more simple. Consider that first example of a Time Slot: *every day from 8AM to 9PM PST*. This includes major holidays, and there is no easy way to define a Time Slot so that the repeating block of time does not appear on major holidays. *Every day from 8AM to 9PM PST except for on multiple arbitrary dates* does not count as a simple pattern.


More complex patterns, such as *every day from 8AM to 9PM PST except for on multiple arbitrary dates including major holidays* are best built out as Availability Schedules. When defining Availability Schedules, a Time Slot like *every first day of the year* can be subtracted from a Time Slot like *every day from 8AM to 9PM PST*, resulting in the more complex Availability Schedule *every day from 8AM to 9PM PST except the first day of the year*. Because Availability Schedules can be constructed out of arbitrarily many Time Slots, there is no limit to how intricate Availability Schedules can become.


Out of the box, Airkit comes with several Time Slots pre-configured. These correspond to regional [TCPA regulations](https://support.airkit.com/docs/tcpa); utilizing them streamlines the process of creating TCPA-compliant apps.


# Stage


The Stage displays a visual representation of the Availability Schedule or Time Slot being accessed in the Tree. This display can take two forms: a calendar, or a chart of timestamps. The Calendar Display will open by default upon selecting an Availability Schedule or Time Slot from the Tree, but you can toggle between the two displays at any time by clicking on the 'Calendar' and 'Chart' icons on the upper left of the stage:


![2021-09-23_15-07-03__1_.gif](./assets_v1714/calendar-builder-v1714-2).gif)


## Calendar Display


The Calendar Display shows what the selected Availability Schedule or Time Slot would look like if presented as events on a weekly calendar, the timezone of which corresponds to the timezone associated with the Availability Schedule or Time Slot. (Note that, depending on the size of the Stage and the web browser more generally, there will not always be room to display the full week, in which case the view can be modified by side scrolling.) You can confirm the timezone of the calendar you are viewing by noting what timezone is marked after "Viewing as" in the upper left of the Stage: 


![2021-09-23_15-10-07.png](./assets_v1714/calendar-builder-v1714-3.png)


For instance, here is what the Calendar Display shows when viewing the Availability Schedule *TCPA - GA - America/New_York* (one of the many Availability Schedules that comes out of the box) on September 23rd, 2021. Note that in compliance with the relevant TCPA regulations, no availability is displayed on Sunday:


![2021-09-23_15-12-29.png](./assets_v1714/calendar-builder-v1714-4.png)


By default, the Calendar Display will set the showcased weekly calendar to the current date and will even mark the current time. (Note, in the above example, that there is a red line marking 14:15 PST: that's the time the screenshot was taken.) If you want to view past or future weeks, use the arrows on the upper right of the Stage. The '<' icon shifts the weekly calendar to the week before the one being displayed; the '>' icon to the week after:


![2021-09-23_15-17-24__1_.gif](./assets_v1714/calendar-builder-v1714-5).gif)


Visualizing how the weekly calendar displays multiple weeks is particularly important when you want to confirm that an Availability Schedule exhibits the desired behavior on holidays.


## Chart Display


The Chart Display shows all Availability Schedules or Time Slots within a given range of times. Unlike the Calendar Display, all dates and times featured in the Chart Display are always in UTC, and you can confirm that this is the timezone you are viewing by noting the timezone is marked after "Viewing as" in the upper left of the Stage:


![2021-09-23_15-20-19.png](./assets_v1714/calendar-builder-v1714-6.png)


By default, this range of times will reflect the range of times show by the Calendar Display upon switching views. For instance, here is what the Chart Display initially shows when viewing the Availability Slot *TCPA - GA - America/New_York* on September 23rd, 2021, assuming the Calendar Display still set to the present week:


![2021-09-23_15-22-14.png](./assets_v1714/calendar-builder-v1714-7.png)


To change the range of dates viewed in the Chart Display, select the desired dates and times from the dropdown menus above the chart:


![2021-09-23_15-23-08__1_.gif](./assets_v1714/calendar-builder-v1714-8).gif)


# Inspector


The Inspector is where you can examine and modify selected Availability Schedules or Time Slots. The appearance and functionality of the Inspector differs depending on which of the two is being inspected.


## Availability Schedules


When examining Availability Schedules, the Inspector displays three expandable and collapsible sections: **Description**, **Date and Time Settings**, and **Time Slots**. 


* **Description** - Write, access, and edit a description of the selected Availability Schedule; this is recommended to make the intended use cases more explicit. The *Description* section is also where you can access and edit a key to associate with the selected Availability Schedule; this key is a shorthand identifier that can be used refer to the Availability Schedule in an [Airscript](https://support.airkit.com/docs/what-is-airscript?) expression.


* **Date and Time Settings** -  Select the reference timezone of the selected Availability Schedule.


* **Time Slots** - Define how and which Time Slots define the Availability Schedule. For more on how to define Time Slots, see the section below.


## Time Slots


When examining Time Slots, the Inspector displays four expandable and collapsible sections: **Description**, **Date and Time Settings**, **Recurrence**, and **Time Slots**. 


* **Description** - Write, access, and edit a description of the selected Time Slot; this is recommended to make the intended use cases more explicit. 


* **Date and Time Settings** - Select the reference timezone of the selected Time Slot.


* **Recurrence** - Define blocks of time as described by simple patterns, such as what time they begin, how long they are, and when they begin repeating (if they do).


* **Capacity** -  Set the number of appointments that can be made to an individual block of time before it is no longer available to schedule further appointments.