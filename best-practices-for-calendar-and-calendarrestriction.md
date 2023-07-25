There are two ways to use [Availability Schedules](https://support.airkit.com/docs/calendar-builder) in a [Scheduler Web Control](https://support.airkit.com/reference/scheduler-web-control): they can be used to set either the **calendar** or the **calendarRestriction**. Note that associating a value with **calendar** entails selecting an Availability Schedule from a dropdown of available options, whereas associating a value with **calendarRestriction** requires entering the key associated with the desired Availability Schedule. 


![2021-09-28_11-56-25.png](./assets_v1714/best-practices-for-calendar-and-calendarrestriction-v1714-0.png)


To look up or even edit the key associated with any individual Availability Schedule, toggle to [Calendar Builder](https://support.airkit.com/docs/calendar-builder) and inspect the Availability Schedule of interest.


A set **calendar** value is required for a scheduler to run as intended. The blocks of time defined by the Availability Schedule selected as the **calendar** are the appointment windows available for users to select.


A set **calendarRestriction** value is optional, but should it be defined, available appointment windows will be restricted to only the blocks of time encompassed by the Availability Schedule associated with **calendarRestriction**.


When used in tandem, the **calendar** value is meant to define day-to-day behavior (such as how long each appointment window is) while the **calendarRestriction** value accounts for holidays and provides a sanity check to ensure the Availability Schedule associated with the **calendar**isn't allowing appointments to be made during off hours. 


Best practices dictate that the Availability Schedules used to define **calendarRestriction** values should not consist of any Time Slots with split slots: the value given by **calendarRestriction** needs to define large blocks of time capable of encompassing smaller ones, not small appointment windows.


### Using pre-configured Availability Schedules to set **calendarRestriction** values


Out of the box, Airkit's [Calendar Builder](https://support.airkit.com/docs/calendar-builder) comes with several Availability Schedules (as well as their component Time Slots) pre-configured. All pre-configured Availability Schedules define the blocks of time in which [TCPA regulations](https://support.airkit.com/docs/tcpa) allow automated calls. Because these regulations vary subtly between states, timezone, and other information regarding locale, each relevant locale has its own associated Availability Schedule. Each follows the same naming convention: they begin with "TCPA", followed by the abbreviation of the relevant state, followed by information on the exact locale, each separated by hyphens.


These pre-configured TCPA Availability Schedules are designed to define **calendarRestriction** values: the blocks of time they define are large and broad, containing no Time Slots with split slots. When used in tandem with a custom-made Availability Schedule as the **calendar** value, a TCPA Availability Schedule ensures that all appointments made with a scheduler will fall within the windows of time allowed by TCPA regulations in the relevant locale.


TCPA Availability Schedules should not be used to set **calendar** values.


### Setting **calendarRestriction**dynamically


Because the value of **calendarRestriction** is set by an [Airscript](https://support.airkit.com/docs/airscript-quick-start)-parsable key – a shorthand [text](https://support.airkit.com/reference/the-text-variable-data-type) identifier that refers to an Availability Schedule as defined in the [Calendar Builder](https://support.airkit.com/docs/calendar-builder) – it can be defined in terms of Airscript functions as well as a hardcoded string.