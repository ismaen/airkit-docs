Activity Explorer Overview
--------------------------


Activity Explorer provides a way to view the events that occur on a session to help troubleshoot and diagnose issues within an application. The Activity Explorer surfaces every journey that occurs in a published application and logs every event and key activity from the user within that journey. Each of these events can then be drilled into to get additional data to help understand what events are firing in a journey, and to help diagnose errors faster. 


Activity Explorer Dashboard
---------------------------


The Activity Explorer dashboard surfaces all of the various logs for each journey in a centralized location.


To get to the Activity Explorer dashboard, go to [console.airkit.com](https://console.airkit.com) and select an application. Then click on '**Activity**' under Manage Your Application. 


![2021-04-16_14-58-17__1_.gif](./assets_v1714/view-past-journeys-with-activity-explorer-v1714-0).gif)


The Activity Explorer consists of the following fields:


* **Branch**: The branch name of the deployed application
* **Deploy**: The deployment key of the application
* **Status**: Status of the journey, whether it is open or closed.
* **Latest Event**: Date and time of the last event to occur on the journey
* **Started Event**: Date and time of when the journey started
* **Closed Event**: Date and time of the event that ended the journey
* **Actions**: Number of actions run in the journey
* **Action Errors**: Number of application errors throughout the journey
* **Runtime Errors**: Number of platform errors throughout the journey
* **Messages**: The number of SMS messages sent in a journey
* **Voice (mins)**: The amount of time spent on a phone call during the journey
* **Journey ID**: Identifier of the journey


To dive deeper into additional logs, click into log instance of a journey which will open up the Activity Summary, which shows all of the events that have happened in the journey. This view provides a way to see errors that occur as well as a chronological view of the events the user has gone through. 


<img src="./assets_v1714/view-past-journeys-with-activity-explorer-v1714-1.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

Filtering and Sorting on Summary Fields
---------------------------------------


Activity Explorer has the ability to add filters and sorting on any of the fields that are surfaced in the dashboard. Filters make it easier to pinpoint what data should be shown on the dashboard and allows users to key in on the journeys that are important.


To add a filter on a specific field, go to Activity Explorer and click on the filter icon. Filters can also be added for a specific field by selecting the dropdown on the field column as well.


<img src="./assets_v1714/view-past-journeys-with-activity-explorer-v1714-2.png" alt="organizing info" style="max-width: 450px; width:100%;"/>

Select a column from the drop down to create a filter on. Then, select the filter operation. The Filter operations include:


* Has a value
* Does not have a value
* Is any of
* Is not any of
* Equals
* Does not equal
* Starts with
* Contains Text


This screenshot below shows how to create a filter to show all journeys with the Status of the journey equal to 'Closed'. There's also the ability to add additional filter operations to create more precise filters. Click on **Apply** to create the filter.

<img src="./assets_v1714/view-past-journeys-with-activity-explorer-v1714-3.png" alt="organizing info" style="max-height:300px"/>

Additionally, to sort the logs in Activity Explorer, click on the sort icon to add sorting and select a column to sort on.

<img src="./assets_v1714/view-past-journeys-with-activity-explorer-v1714-4.png" alt="organizing info" style="max-height:275px"/>

Further Reading
---------------


Activity Explorer is a great tool to dive deeper into the journeys that an application's users are going through and provides further insights to debug errors. For more information on analytics within Airkit, see:


* [Journey Analytics in Airkit](https://support.airkit.com/docs/journey-analytics)
* [The Reporting Metric > Count Action](https://support.airkit.com/reference/the-reporting-metric-count-action)
* [The Reporting Metric > Field Action](https://support.airkit.com/reference/the-reporting-metric-field-action)
* [The Reporting Metric > Statistic Action](https://support.airkit.com/reference/the-reporting-metric-statistic-action)
* [The Reporting Metric > Start Timer Action](https://support.airkit.com/reference/the-reporting-metric-start-timer-action)
* [The Reporting Metric > Stop Timer Action](https://support.airkit.com/reference/the-reporting-metric-stop-timer-action)
* [The Reporting Metric > Log Custom Event Action](https://support.airkit.com/reference/log-custom-event-action)