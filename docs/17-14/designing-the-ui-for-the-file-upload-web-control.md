Building the UI
---------------


The [File Upload](https://support.airkit.com/reference/file-upload-web-control) Web Control, unlike other Web Controls, doesn't have a default appearance. When it is first added to a Web Page, it will appear in the Stage as follows:

<img src="./assets_v1714/designing-the-ui-for-the-file-upload-web-control-v1714-0.png" alt="organizing info" style="max-width: 350px; width:100%;"/>

Other Web Controls can then be nested inside the File Upload Web Control in the same ways they might be added to any other [Container](https://support.airkit.com/reference/container-web-control):


<img src="./assets_v1714/designing-the-ui-for-the-file-upload-web-control-v1714-1.gif" alt="organizing info" style="max-width: 400px; width:100%;"/>

They can also be styled like nested Web Controls in any other [Container](https://support.airkit.com/reference/container-web-control). 


Once a Web Control has been made a nested component of the File Upload Control, clicking on it will generally result in a prompt to select an item for upload, after which downstream [Events](https://support.airkit.com/docs/events) associated with the File Upload Control will be triggered.


#### A note on which Web Controls to use as component parts


As discussed above, after a Web Control has been made a nested component of the File Upload Control, clicking on it will generally result in a prompt to select an item for upload. However, there are some Web Controls, such as [Buttons](https://support.airkit.com/reference/button-web-control) and [Input Boxes](https://support.airkit.com/reference/text-input-web-control), that are structured around supporting particular user interactions, and these interactions will take precedence over uploading a file.


It is possible, for instance, to include a [Button](https://support.airkit.com/reference/button-web-control) as part of a File Upload Web Control and associate clicking that button with an [Action Chain](https://support.airkit.com/docs/action-builder). A user that clicks that Button, then, would not be prompted to select an item for upload and would instead trigger the Action Chain associated with the Button.


To ensure that the functionality of a File Upload Web Control will always be accessible to users, we recommend including at least one [Label](https://support.airkit.com/reference/label-web-control) in every File Upload Web Control (perhaps on that says something like "+ New File"). Labels are not designed to facilitate any user interaction other than reading, and so they do not contain the framework of anything that might override the functionality of the File Upload Web Control.


Examples and Discussion
-----------------------


For a deeper dive into how to apply the File Upload Web Control, check out the following video. It discusses how to create progress bars, display thumbnails, and store any number of files uploaded to the same Control:
[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FmbdBMB9B--Q%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DmbdBMB9B--Q&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FmbdBMB9B--Q%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=mbdBMB9B--Q",
  "title": "File upload control",
  "favicon": "https://www.youtube.com/s/desktop/15c06292/img/favicon.ico",
  "image": "https://i.ytimg.com/vi/mbdBMB9B--Q/hqdefault.jpg"
}
[/block]