Reading and writing data from external systems from Connection Builder
----------------------------------------------------------------------


Integrations enable the application read and write data from external systems using the [HTTP request Data Operation](https://support.airkit.com/reference/http-request-data-operation) in a [Data Flow](https://support.airkit.com/docs/data-flows). The HTTP Request data operation can be used to call any web API such as a REST service or SOAP service, and can also be used with an authenticated integration. This section will walk through how to retrieve tweets using the Twitter API with an [authenticated integration](https://support.airkit.com/docs/setting-up-integrations).


1. Go to **Connection Builder** and add a **Data Flow**.  
  
![mceclip9.png](./assets_v1714/querying-and-manipulating-data-from-external-systems-v1714-0.png)
2. Choose the [**HTTP Request** data operation](https://support.airkit.com/reference/http-request-data-operation).  
![mceclip3.png](./assets_v1714/querying-and-manipulating-data-from-external-systems-v1714-1.png)
3. In the Service dropdown, select the integration that you added in Configuration Builder. This example will cover connecting to the Twitter integration created using OAuth.  
  
![mceclip4.png](./assets_v1714/querying-and-manipulating-data-from-external-systems-v1714-2.png)
4. Now this HTTP Request data operation will retrieve the access tokens using your integration and allow you to call the Twitter API. Here we are doing a search across tweets using the search endpoint looking for 'airkitcx'. After running a test against the endpoint by hitting the play icon, the results will populate in the Run Results area.   
  
![mceclip5.png](./assets_v1714/querying-and-manipulating-data-from-external-systems-v1714-3.png)


Once the Data Flow is created with the HTTP Request, the data flow is usable throughout the journey.


Reading and writing data with scheduled jobs
--------------------------------------------


[Periodic Task](https://support.airkit.com/docs/setting-up-periodic-tasks) can be used to read and write data from an external system in a recurring fashion. For example, if you wanted to check for new tweets every hour, you would set up a [Data Flow](https://support.airkit.com/docs/data-flows) first and connect the Periodic Task to that Data Flow. To create a Periodic Task, go to [Connection Builder](https://support.airkit.com/docs/connection-builder) and click '**+**' next to Periodic Tasks.  
![reading_writing_scheduled1.png](./assets_v1714/querying-and-manipulating-data-from-external-systems-v1714-4.png)  
Then, choose your **Connection** which is referring to the Data Operation you created.


![reading_writing_2.png](./assets_v1714/querying-and-manipulating-data-from-external-systems-v1714-5.png)  
Define the schedule that you would like your Periodic Task to run. This field uses [cron schedule expressions](https://crontab.guru/) and the times are based in UTC. Once the Periodic Task is set up, you can save and publish your app to start your scheduled jobs!


Next Steps
----------


This article covered how to make outbound requests in an application. To configure inbound requests to an application, see [Push data from Airkit to external systems](https://support.airkit.com/docs/passing-data-from-external-systems).