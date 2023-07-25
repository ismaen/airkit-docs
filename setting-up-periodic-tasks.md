Overview
--------


Periodic Tasks provide a simple way of scheduling [Data Flows](https://support.airkit.com/docs/data-flows). This way, users can define when and how often a specific Data Flow should be run within the App.


Setting up a Periodic Task
--------------------------


From the [Connection Builder](https://support.airkit.com/docs/connection-builder), Periodic Tasks can be set up by clicking on the ‘+’ sign next to Periodic Tasks.


<img src="./assets_v1714/setting-up-periodic-tasks-v1714-0.png" alt="organizing info" style="max-width: 500px; width:100%;"/>


This example will use a Periodic Task to regularly send account managers a report with the App’s CSAT survey results.

<img src="./assets_v1714/setting-up-periodic-tasks-v1714-1.png" alt="organizing info" style="max-width: 300px; width:100%;"/>


In the inspector, select the a Data Flow to be scheduled. In Period, set the scheduling criteria and in Time Zone, select the corresponding time zone. 


The Period input expects a cron schedule expression. For help with cron schedule expressions, see <https://crontab.guru/>. 


Once created, the Data Flow will run at 10, Chicago time, every Monday.


Formatting the Period of time
-----------------------------


In order to set the frequency for a Data Flow to be run, the five ‘*’ characters should be replaced in Period following this [format](https://crontab.guru/):

* The first * corresponds to the minutes
* The second * corresponds to the hour(s)
* The third * corresponds to the day(s) of the month
* The fourth * corresponds to the month(s)
* The fifth * corresponds to the day(s) of the week


You can also use special characters or non-standard values to make a more accurate call:

<img src="./assets_v1714/setting-up-periodic-tasks-v1714-2.png" alt="organizing info" style="max-width: 300px; width:100%;"/>


Tracking logs
-------------

In the Stage section when editing a Periodic Task, you can see a log of all Periodic Tasks that have been run.