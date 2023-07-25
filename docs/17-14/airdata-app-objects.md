AirData App Objects are a way to group sets of variables together to create a more complex object. Each object in an AirData App Object is addressed by a text string and can contain any [Airkit Variable Type](https://support.airkit.com/reference/data-types-overview) including other AirData App Objects.


### Defining AirData App Objects


Defining AirData App Objects happens in [Data Builder](https://support.airkit.com/docs/data-builder). Creating an App Object is as simple as clicking the + button at the top of the *Tree*. Select *App Object*. Rename an App Object by double-clicking the name in the *Tree* and editing it.


Here is an example of a simple app object with four properties.


![AirData.png](./assets_v1714/airdata-app-objects-v1714-0.png)


By clicking plus icon on an App Object, additional properties can be added to any app object. Any supported [Data Type](https://support.airkit.com/reference/data-types-overview) can be added. Rename a property by double-clicking on it in the *Tree*.


In addition to to the properties explicitly defined as part of an App Object, each App Object is also given a another property: **__id**, which serves as a unique identifier for each App Object instance. A unique **__id** value is automatically assigned whenever an App Object instance is added to AirData. To display this property more explicitly, add a text property and call it "__id": 


![ezgif.com-gif-maker.gif](./assets_v1714/airdata-app-objects-v1714-1.gif)


Note that even though the three displayed App Object instances in the above example are largely blank, they have still been assigned unique **__id** values, and were assigned these values even before the **__id** property was explicitly displayed.


Calling an App Object instance based on its **__id** is valuable when the instance needs to be specific and unique, such as, for example, when declaring which instance will be deleted as part of an [AirData Request](https://support.airkit.com/reference/airdata-request-data-operation). Under most other circumstances, it is safe for this unique identifier to be abstracted away, which is why it is not displayed in AirData by default. However, regardless of whether it is explicitly displayed in AirData, it can be used in practice the same way as any other object property.


### Using a Defined App Object


Once defined, an App Object can be used as a type anywhere a variable can be declared, such as on a Web Flow, Web Page, or in a Data Flow as an input or variable type.


![TeacherObject.png](./assets_v1714/airdata-app-objects-v1714-2.png)


Expression Editors in Card and Card Views also have the added benefit of including some type inference allowing for autocomplete with properties of strongly typed *App Objects*.


![TypeAhead.png](./assets_v1714/airdata-app-objects-v1714-3.png)


Hitting tab in this instance would complete the teacher property of **firstName**.