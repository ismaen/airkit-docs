The [Maps Control](https://support.airkit.com/reference/map-web-control) provides the ability to integrate and display a map within Airkit, building out applications that leverage addresses and a user's location. For example, the maps control is useful for building out experiences that display a map for a specific location, finding nearby businesses, or to pinpoint a current user's location. This article will walk through the following:


* [Display a map of a single location](#h_01F2Q50FJQ2YWSKVREVSAD7S3Q)
* [Display multiple locations on a map](#h_01F2Q50PERY1SY1BGKRA87Z418)


Display a map of a single location
----------------------------------


The Map Control is used to display a single location in an application. This is great for showing users where a specific location is on a map, such as a home or business location. This section will walk through how to add a map to an application and show a single location that is marked, specifically the Chase Center in San Francisco, CA. 


First, in the Web Page, add the Maps Control. By default, Maps will display a view of Palo Alto. 


<img src="./assets_v1714/working-with-maps-v1714-0.png" alt="organizing info" style="max-width: 400px; width:100%;"/>

With the map control selected in the tree, go to the inspector and change both the **Center** property and the **Markers** property to the List of objects below. The **Center** property expects a single object containing the latitude and longitude properties like so:





```javascript Airscript
{  
  "latitude":37.7680466,  
  "longitude":-122.387715  
}
```



  
The **Markers** property expects a List of Objects, like so:





```javascript Airscript
[{  
  "latitude":37.7680466,  
  "longitude":-122.387715  
}]
```



  
The **Center** property will center the map around the location object that is passed. The **Markers** will place the 'teardrop' markers at the locations of the List of Objects passed. 


<img src="./assets_v1714/working-with-maps-v1714-1.png" alt="organizing info" style="max-width: 275px; width:100%;"/>

For more information on all of the map control properties, see [Map Web Control.](https://support.airkit.com/reference/map-web-control)Also, to display a location indicator for the current user's location, see [Working with the Users Current Location](https://support.airkit.com/docs/working-with-the-users-current-location).


Display multiple locations on a map
-----------------------------------


The maps control also supports showing multiple locations within the control. Displaying multiple locations is useful for showing nearby points of interests or even loading multiple locations into a map from AirData. This section will walk through how to build out both of those experiences within an application.


* [Searching for nearby points of interest](#h_01F2MTM6QCNGY7QVHX7Y2KVKZQ)
* [Loading locations from AirData](#h_01F2Q52JZ6D1A4V0DDT1C1CRP7)


### Searching for nearby points of interest


Searching for nearby points of interest can be used within a journey to look for nearby restaurants, or locate the nearest car repair shop. This example will walk through how to build out a search experience to find nearby gas stations. 


In the web page of the application, add a [Place Search](https://support.airkit.com/reference/place-search-input-web-control) control and a [Map](https://support.airkit.com/reference/map-web-control) control. The place search control will be where users can type and search for what kind of gas stations are nearby, and the Map control is used to display the locations of those gas stations.


<img src="./assets_v1714/working-with-maps-v1714-2.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

Then create a [Place app object](https://support.airkit.com/reference/the-location-data-type) in AirData, which is a pre-defined location object that includes the following properties:


* latitude
* longitude
* name
* identifier
* formatted_address
* icon


![2021-04-05_19-29-22__1_.gif](./assets_v1714/working-with-maps-v1714-3).gif)


To do this, go to **Data Builder**, then click on the '+' icon and click on **Add Place**. For this example, rename the **Place** object to 'Place'. Then save the application. 


After saving the application, go the web page in Web Builder and add the following variables with the associated types:


* **location**: Place
* **nearby_poi**: List of Places


<img src="./assets_v1714/working-with-maps-v1714-4.png" alt="organizing info" style="max-width: 300px; width:100%;"/>

Then, on the **Place Search Input** control, bind the `location` variable to the location property, **placeType** to `gas_station`, **nearby_poi** to `searchResults`, change the **searchType** to `nearby`, and **rankBy** to `distance`. By binding the `location` variable to the location property, allows the control to prefer results in the specified area that is passed by the `location` variable. Also by binding **nearby_poi** to `searchResults`, allows the results to be surfaced as an array/list. Lastly, by adding the string `gas_station` to **placeType**, this will return that particular type of place. For additional information on place types, see the [Places API](https://developers.google.com/maps/documentation/places/web-service/supported_types) by Google. 


<img src="./assets_v1714/working-with-maps-v1714-5.png" alt="organizing info" style="max-width: 300px; width:100%;"/>

Under the **Actions** tab on the Place Search Input control, use the Set Variable action to set **nearby_poi** to `event.value`.    

<img src="./assets_v1714/working-with-maps-v1714-6.png" alt="organizing info" style="max-width: 300px; width:100%;"/>

After finishing configuring the Place Search Input, click on the Map control and go to the General tab in the inspector. In the **Markers** property, add `nearby_poi`*. In the center property, add `location`. 


<img src="./assets_v1714/working-with-maps-v1714-7.png" alt="organizing info" style="max-width: 300px; width:100%;"/>

**Note**: To identify the current location that the map is using to find nearby gas stations, check the showIndicator property.  

![mceclip8.png](./assets_v1714/working-with-maps-v1714-8.png) 


After saving the application, go to App preview to test out your app. The map will automatically add markers to the nearby gas stations based on your location. The search input box can be used to refine a specific gas station brand, or you can hide the place search control from view to just show the nearby gas stations in a specified radius without allowing the user to alter it. If the application was purely used for searching across any points of interest, the placeType property can be left blank on the place search input control. 


<img src="./assets_v1714/working-with-maps-v1714-9.png" alt="organizing info" style="max-width: 300px; width:100%;"/>

### Loading locations from AirData


The map control can also be used to mark locations that are stored in AirData or other external systems. This example will walk through how to load locations from AirData and mark those locations on a map. 


In order to load locations from AirData to a map, there has to be an App object to store the data, as well as some location data points. The data points that will be used are nearby parks relative to a specific location in Palo Alto. 


First, go to AirData and create a [Place object](https://support.airkit.com/reference/the-location-data-type) and name it 'Parks'. This is where the locations to mark on the map will be stored.


<img src="./assets_v1714/working-with-maps-v1714-10.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

Next, add some locations to the Parks app object. In order for the maps control to mark locations, it requires the latitude and longitude of the location. This can either be done manually or through a [Data Flow.](https://support.airkit.com/docs/data-flows)


#### Adding locations to AirData through a DataFlow


To add locations through a Data Flow, create a Data Flow, name it '**Insert Parks**' and add an input of the type 'List of Parks'. Name the input variable to '**parks**'.


![2021-04-06_11-40-52__1_.gif](./assets_v1714/working-with-maps-v1714-11).gif)


Below is some sample park data that will be inserted into the Parks App Object. Copy and paste the sample data into the **parks** input variable created in the previous step.




```javascript Airscript
[  
  {  
    "latitude": 37.42967099999999,  
    "longitude": -122.1410736,  
    "formattedAddress": "Palo Alto",  
    "identifier": "",  
    "name": "Jerry Bowden Park",  
    "icon": "https://maps.gstatic.com/mapfiles/place_api/icons/v1/png_71/park-71.png"  
  },  
  {  
    "latitude": 37.42578719999999,  
    "longitude": -122.1427593,  
    "formattedAddress": "202 Ash Street, Palo Alto",  
    "identifier": "",  
    "name": "Sarah Wallis Park",  
    "icon": "https://maps.gstatic.com/mapfiles/place_api/icons/v1/png_71/park-71.png"  
  },  
  {  
    "latitude": 37.431507,  
    "longitude": -122.147651,  
    "formattedAddress": "1899 Park Boulevard, Palo Alto",  
    "identifier": "",  
    "name": "Peers Park",  
    "icon": "https://maps.gstatic.com/mapfiles/place_api/icons/v1/png_71/park-71.png"  
  }  
]
```



 
Then add an [AirData Data Operation](https://support.airkit.com/reference/airdata-request-data-operation), Pselect the 'Parks' App Object, and select the INSERT type. Lastly add the 'Parks' input variable as the object to insert. The Data operation should look like below:

<img src="https://a01-support.airkit.com/working-with-maps/mceclip1%20(1).png" alt="organizing info" style="max-width: 350px; width:100%;"/>

Click on the 'play' icon, which should insert the three parks into the Park app object. Now there is data to retrieve from the application. 

#### **Retrieving Parks to Display on the Map**


Now that there is data in the Parks App object, it can be passed to the Maps control using a Data Flow.  The Data Flow will simply be a query to the Parks App object, which will then pass the list of parks as the output of the Data Flow. 


First, add a Data Flow in Connection builder, name it 'Retrieve Parks' and add an AirData Operation. Select the Parks App Object and choose the type 'Query'.

<img src="https://a01-support.airkit.com/working-with-maps/mceclip2%20(1).png" alt="organizing info" style="max-width: 350px; width:100%;"/>



Then, add a [Transform data operation](https://support.airkit.com/reference/the-transform-data-operation)and use: 



```javascript Airscript
objectService.results
```

for the transform expression. This will parse out only the results from the query, which is needed to mark locations on the map. Also, change the variable Type to '**List of Parks**'.


<img src="./assets_v1714/working-with-maps-v1714-12.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

Lastly, pass the transform variable as the return value at the end of the Data Flow. 


<img src="./assets_v1714/working-with-maps-v1714-13.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

#### Displaying Locations on the Map


Now that the application has a Data Flow configured to retrieve parks from AirData, the parks can be passed to the maps control. For this example, the Data Flow will run on the Card Updated event, but the parks can be retrieved through any other events or actions using the Data Flow. First, add a variable on the web page with the type 'List of Parks' and name the variable **parks**.


<img src="./assets_v1714/working-with-maps-v1714-14.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

Then click on the Actions tab on the web page, and under the Card Updated event, add a 'Run Data Flow' action. Select the Data Flow created in the previous step to retrieve parks and bind the output to the **parks** variable. 


<img src="./assets_v1714/working-with-maps-v1714-15.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

After configuring the Data Flow, add a [Map control](https://support.airkit.com/reference/map-web-control) to the web page. With the map control selected, go to the inspector under the General tab, and enter in the following for their respective properties:


* markers: **parks**
* center:




```javascript Airscript
{  
  "latitude":37.4404217,  
  "longitude":-122.1476691  
}
```

<img src="./assets_v1714/working-with-maps-v1714-16.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

This will pass in the list of parks and mark them on the map as well as hardcode the center of the map to be at that specific location. As an optional step, check the **showIndicator** property to make the indicator visible. After configuring the map control properties, go to App Preview and see the three marked parks on the map.



<img src="./assets_v1714/working-with-maps-v1714-17.png" alt="organizing info" style="max-width: 200px; width:100%;"/>