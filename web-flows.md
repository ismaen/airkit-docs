# What is a Web Flow?


Web Flows are containers for Web Pages. Within a [Journey](doc:journeys) there can be arbitrarily many Web Flows that are each built with a specified purpose. Each Web Flow can contain one or many Web Pages. Web Flows might be considered the individual processes or workflows within a Journey, while Web Pages are the steps within each process. 


Web Flows can be illustrated by the following example:


There's a digital appointment scheduling application that will capture a user's information in a form. After the information is collected, the application will ask the user to schedule an appointment by selecting an appointment time. There are two Web Clows that exist here:


* Capturing the user's information
* Scheduling the appointment


![mceclip0.png](./assets_v1714/web-flows-v1714-0.png)


The reason that these two tasks are constructed as two separate Web Flows is because each of them can be considered a standalone process. Designated these Web Flows as separate enables developers to create more modular experiences. This makes it possible connect the Web Flows via Events or to use the Web Flows as modals. 


# When to use a Web Flow vs Web Page

An application can technically be built with only Web Pages, but it is generally recommended and a best practice to leverage Web Flows when building out an application. Use Web Flows to organize and compartmentalize various processes in a Journey. Typically, when there is a separate process in a Journey that can potentially be re-used, then you should compartmentalize it in Web Flow. 

# Events and Web Flows

Events can be used to link Web Flows to each other, serving as a bridge that connects multiple Web Flows resulting in the overall Journey.  The [Go To Web Flow Action](https://support.airkit.com/reference/navigate-to-web-flow-action) can be used to connect Web Flows together. Leveraging events provide a mechanism that allows the Web Flow to be reused and also diagram meaningful actions connected by events in Journey Builder.