When connecting an application with other external systems to write back addresses, oftentimes there will be specific address formats that are accepted. The location components provide a few different outputs of addresses that can be used throughout the journey, to either be used as a variable or written back to other external systems like Salesforce. They can also be used to auto populate form fields that require separate address fields as well. Below are some of the different address formats the are retrievable:


**Latitude and Longitude**



```javascript Airscript
{   
  "latitude": 37.42854870000001,   
  "longitude": -122.1420041   
}
```

**formattedAddress**:



```
200 California Ave, Palo Alto, CA 94306, USA
```

Note: To split the formattedAddress into different address components (i.e. Address line, City, State, Zip Code), the [SPLIT()](https://support.airkit.com/reference/split) Airscript function can be used to break the address apart. 



```javascript Airscript
SPLIT(formattedAddress,",")
```

**addressComponents**:



```json Airscript
"addressComponents": {   
  "address": "200 California Ave",   
  "city": "Palo Alto",   
  "state": "CA",   
  "zip": "94306",   
  "country": "US"   
}
```

Getting different address formats using the Place Search Input control
----------------------------------------------------------------------


The [Place Search Input control](https://support.airkit.com/reference/place-search-input-web-control) can provide the three different types of address formats based off of what address is searched. The maps control can get the latitude/longitude and formattedAddress of a location, but does not provide addressComponents. For information on how to use the maps control and store the location as a variable, see [Working with the Users Current Location](https://support.airkit.com/docs/working-with-the-users-current-location). 


The place search input control, built on top of the [Places API](https://developers.google.com/maps/documentation/places/web-service/search) by Google, can be used to search for specific addresses, places by categories, points of interest, and more. When configured, the control will provide the latitude, longitude, formatted address, addressComponents, identifier, name, and icon.


First, add a Place Object in AirData and name it **Place**.  


![appobjectPlace__2__copy.gif](https://a01-support.airkit.com/working-with-different-address-formats/appobjectPlace%20(2)%20copy.gif)


Then add a variable of the type '**Place**' on the web page. Click on the '**+**' icon next to variables in the inspector, go to **objects**, and select **Place**. Name the variable **location**. Add another variable with the type 'List of Place' and name it **search_results**.  This example will give the option to surface to location data objects.


![mceclip0.png](https://a01-support.airkit.com/working-with-different-address-formats/mceclip0.png)


Once the variables are added, add the Place Search Input control on the web page. 


![mceclip1.png](https://a01-support.airkit.com/working-with-different-address-formats/mceclip1.png)


Then select the Place Search Input control, and under the General tab in the inspector,  change the searchType to **autocomplete**. 


![mceclip4.png](https://a01-support.airkit.com/working-with-different-address-formats/mceclip4.png)


Go to the Actions tab in the inspector, and under the 'Search Results Changed' event, add the [Set Variable action](https://support.airkit.com/reference/the-set-variable-action) and bind **search_results** to **event.value**. 


![mceclip3.png](https://a01-support.airkit.com/working-with-different-address-formats/mceclip3.png)


Now that **search_results** is bound to **event.value**, this will provide the ability to search for an address and bind the selected address that is searched to the **search_results** variable. To see the output, save the application and go to **App Preview** and search for an address. The output will look similar to the below. This output includes the latitude/longitude, formattedAddress, and the addressComponents and can be used to pass to other systems. 



```json Airscript
[  
  {  
    "latitude": 37.4285713,  
    "longitude": -122.1434025,  
    "formattedAddress": "200 California Ave, Palo Alto, CA 94306, USA",  
    "addressComponents": {  
      "address": "200 California Ave",  
      "city": "Palo Alto",  
      "state": "CA",  
      "zip": "94306",  
      "country": "US"  
    },  
  "identifier": "<identifier>",  
  "name": "200 California Ave",  
  "icon": "https://maps.gstatic.com/mapfiles/place_api/icons/v1/png_71/geocode-71.png"  
  }  
] 
```

**Additional**: If there was a requirement to get the formattedAddress and bind it to a variable, use the Set Variable action under results changed and bind the **location** variable to **search_results[0].formattedAddress.**


**![mceclip5.png](./assets_v1714/working-with-different-address-formats-v1714-0.png)**


Lastly, to get the value of the place search input control to change to the selected address, add another Set variable action after the above action and bind **place_search_input**variable (auto bound variable for the place search input control) to the **location** variable. 


![mceclip6.png](./assets_v1714/working-with-different-address-formats-v1714-1.png)