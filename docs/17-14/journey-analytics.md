Airkit's out of the box reporting and analytics features provide a way to gather data on user interactions and gain insights on how users are utilizing an application. When leveraging reporting metrics, you can track any type of user interaction, including button clicks using the [counter metric](https://support.airkit.com/reference/the-reporting-metric-count-action) or specific statistics such as CSAT scores using the [statistic metric](https://support.airkit.com/reference/the-reporting-metric-statistic-action). There are also automatic metrics that are tracked and stored on a per journey basis and can be surfaced through a data export. The metrics and journey data can then be pushed to other reporting tools such as Power BI, SnowFlake, and more for further reporting. 


Metric Types
------------


There are two different types of metrics that can be recorded within a journey -- automatic metrics and custom metrics. These metrics can be used in conjunction to build out reports and tie together data for more wholistic insights. 


### Automatic Metrics


Automatic metrics are built in metrics that are captured per journey and can be surfaced through an export in the reporting console. The automatic metrics include data such as SessionId, ActionRuns, UserAgent.DeviceClass and much more. For example, this data is great for creating reports to surface how many total journeys the application has had per deployment, or insights into what type of device the application is accessed on. 


### Custom Metrics


Custom metrics are used to gather data on how an application is being used or any other data that needs to be captured in a report. For example, custom metrics can be used to capture a CSAT score per session or can be used to see how long a user is on a specific web page for. The custom metrics are surfaced in the export along with the automatic metrics. The following custom metrics actions are available to use within an application:


* [Reporting Metric > Count](ref:the-reporting-metric-count-action) 
* [Reporting Metric > Field](ref:the-reporting-metric-field-action) 
* [Reporting Metric > Statistic](ref:the-reporting-metric-statistic-action) 
* [Reporting Metric > Start Timer](ref:the-reporting-metric-start-timer-action) 
* [Reporting Metric > Stop Timer](ref:the-reporting-metric-stop-timer-action) 
* [Log Custom Event](ref:log-custom-event-action) 


Exporting
---------


In the reporting console, there is the ability to export all of the metrics to a .csv to use with other tools. To export, go to an application at [console.airkit.com](https://console.airkit.com) > Click on **Reports.** 

<img src="./assets_v1714/journey-analytics-v1714-0.png" alt="organizing info" style="max-height:350px"/>

Then click on the **Export** button on the top right hand corner. This will generate an export link that will download a .CSV file with the app metric data. 


![2021-04-01_16-57-51__1_.gif](./assets_v1714/journey-analytics-v1714-1).gif)


Leveraging Analytics in your Application
----------------------------------------


Both custom and automatic metrics provide a way to create data driven decisions on how to improve the application workflow or get visibility into KPIs that are trackable throughout a journey. Below are some examples on how to leverage Journey Analytics in Airkit:


* Capturing a CSAT score using the [statistic metric](https://support.airkit.com/reference/the-reporting-metric-statistic-action) and tying it back to a user session.
* Track how long it takes for a user to get through a journey or a specific web flow using the [start timer metric](https://support.airkit.com/reference/the-reporting-metric-start-timer-action) and [stop timer metric](https://support.airkit.com/reference/the-reporting-metric-stop-timer-action).
* Get the average amount of interactions a user has with a chat bot in a conversation using the [count metric](https://support.airkit.com/reference/the-reporting-metric-count-action).


### Reference: Automatic Metric Properties


* SessionId
* OrganizationId
* AppId
* BranchId
* DeployId
* CxrVersion
* SessionTime
* SessionEndTime
* LatestEventTime
* SessionCount
* MessagesSent
* MessagesReceived
* MessagesDelivered
* MessageDeliveryFailures
* VoiceSent
* VoiceReceived
* VoiceDuration
* CanvasLinkOpen
* SocketConnections
* SocketDisconnections
* CallCompletions
* CallDuration
* BridgeCallCompletions
* BridgeCallDuration
* TotalSessionDuration
* EventsOccurred
* ErrorsThrown
* ConnectionsRun
* TriggersRegistered
* TriggersExpired
* TriggersInvoked
* ActionErrors
* ActionRuns
* RuntimeErrors
* MinScreenSizeWidth
* MinScreenSizeHeight
* MaxScreenSizeWidth
* MaxScreenSizeHeight
* HttpSource
* IsDebug
* UserAgent.DeviceClass
* UserAgent.DeviceBrand
* UserAgent.DeviceName
* UserAgent.OperatingSystemClass
* UserAgent.OperatingSystemName
* UserAgent.OperatingSystemVersion
* UserAgent.OperatingSystemVersionMajor
* UserAgent.OperatingSystemNameVersion
* UserAgent.OperatingSystemNameVersionMajor
* UserAgent.LayoutEngineClass
* UserAgent.LayoutEngineName
* UserAgent.LayoutEngineVersion
* UserAgent.LayoutEngineVersionMajor
* UserAgent.AgentClass
* UserAgent.AgentName
* UserAgent.AgentVersion
* UserAgent.AgentVersionMajor
* UserAgent.AgentNameVersion
* UserAgent.AgentNameVersionMajor