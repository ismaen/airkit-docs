The HTML code below is ready to be used within the PDF Data Operation. Please refer to [How to Create a PDF](https://support.airkit.com/docs/creating-a-pdf) on how to use this HTML.


Copy the below code into your PDF Data Operation. Please note that all quotation marks have been escaped in order to be digested by the Airkit platform.


You can see the Original HTML further below.



```html
<!doctype html>
<html>
<!-- START: Invoice -->
<head>
    <meta charset=\\"utf-8\\">
    <title>Invoice</title>

    <style>
    .invoice-box {
        max-width: 800px;
        margin: auto;
        padding: 25px;
        border: 1px solid #eee;
        box-shadow: 0 0 10px rgba(0, 0, 0, .15);
        font-size: 12px;
        line-height: 18px;
        font-family: 'Helvetica Neue', 'Helvetica', Helvetica, Arial, sans-serif;
        color: #555;
    }

    .invoice-box table {
        width: 100%;
        line-height: inherit;
        text-align: left;
    }

    .invoice-box table td {
        padding: 5px;
        vertical-align: top;
    }

    .invoice-box table tr td:nth-child(2) {
        text-align: right;
    }

    .invoice-box table tr.top table td {
        padding-bottom: 20px;
    }

    .invoice-box table tr.top table td.title {
        font-size: 45px;
        line-height: 45px;
        color: #333;
    }

    .invoice-box table tr.information table td {
        padding-bottom: 40px;
    }

    .invoice-box table tr.heading td {
        background: #eee;
        border-bottom: 1px solid #ddd;
        font-weight: bold;
    }

    .invoice-box table tr.details td {
        padding-bottom: 20px;
    }

    .invoice-box table tr.item td{
        border-bottom: 1px solid #eee;
    }

    .invoice-box table tr.item.last td {
        border-bottom: none;
    }

    .invoice-box table tr.total td:nth-child(2) {
        border-top: 2px solid #eee;
        font-weight: bold;
    }

    @media only screen and (max-width: 600px) {
        .invoice-box table tr.top table td {
            width: 100%;
            display: block;
            text-align: center;
        }

        .invoice-box table tr.information table td {
            width: 100%;
            display: block;
            text-align: center;
        }
    }

    /\*\* RTL \*\*/
    .rtl {
        direction: rtl;
        font-family: Tahoma, 'Helvetica Neue', 'Helvetica', Helvetica, Arial, sans-serif;
    }

    .rtl table {
        text-align: right;
    }

    .rtl table tr td:nth-child(2) {
        text-align: left;
    }
    </style>
</head>

<body>
    <div class=\\"invoice-box\\">
        <table cellpadding=\\"0\\" cellspacing=\\"0\\">
            <tr class=\\"top\\">
                <td colspan=\\"2\\">
                    <table>
                        <tr>
                            <td class=\\"title\\">
                                <img src=\\"https://s2-cdn.greenhouse.io/external\_greenhouse\_job\_boards/logos/400/817/300/resized/Airkit-Symbol-RGB-Gradient.png?1568405564" style=\\"width:30%; max-width:300px;\\">
                            </td>
                            <td>
                              <br>
                                Avengers, Inc.<br>
                                890 Fifth Avenue<br>
                                Manhattan, NY 10021
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
            <tr class=\\"information\\">
                <td colspan=\\"2\\">
                    <table>
                      <hr>
                        <tr>
                            <td>
                                Super Person<br>
                                John Doe<br>
                                john@email.com
                            </td>
                            <td>
                                Invoice #: AAC-023745<br>
                                Created: November 3, 2020<br>
                                Due: February 1, 2021
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>

            <tr class=\\"heading\\">
                <td>
                    Payment Method
                </td>

                <td>
                    CC # (last 4 digits)
                </td>
            </tr>

            <tr class=\\"details\\">
                <td>
                    Credit Card
                </td>

                <td>
                    1000
                </td>
            </tr>

            <tr class=\\"heading\\">
                <td>
                    Item
                </td>

                <td>
                    Price
                </td>
            </tr>

            <tr class=\\"item\\">
                <td>
                    Hulk foam fists
                </td>

                <td>
                    $30.00
                </td>
            </tr>

            <tr class=\\"item\\">
                <td>
                    Avengers Subscription (1 year)
                </td>

                <td>
                    $75.00
                </td>
            </tr>

            <tr class=\\"item last\\">
                <td>
                    Captain America shield
                </td>

                <td>
                    $50.00
                </td>
            </tr>

            <tr class=\\"total\\">
                <td></td>

                <td>
                   Total: $155.00
                </td>
            </tr>
          </table>
          <br><br>
          <table>
            <tr>
                  <td>Signature: </td>
            </tr>
            <td>
            <tr><img width=\\"300\\" height=\\"100\\" src=\\"https://www.airkit.com/wp-content/uploads/2020/09/airkit.logo\_.svg\\" /></td></tr>
            <tr>
              <td>Print Name: <b>My Name</b></td>
            </tr>
        </table>
    </div>
</body>
</html>

```



---


Here is the original HTML Code. This is the unescaped example that you can import into a text editor to modify to your needs.



```html
<!doctype html>
<html>
<!-- START: Invoice -->
<head>
    <meta charset="utf-8">
    <title>Invoice</title>

    <style>
    .invoice-box {
        max-width: 800px;
        margin: auto;
        padding: 25px;
        border: 1px solid #eee;
        box-shadow: 0 0 10px rgba(0, 0, 0, .15);
        font-size: 12px;
        line-height: 18px;
        font-family: 'Helvetica Neue', 'Helvetica', Helvetica, Arial, sans-serif;
        color: #555;
    }

    .invoice-box table {
        width: 100%;
        line-height: inherit;
        text-align: left;
    }

    .invoice-box table td {
        padding: 5px;
        vertical-align: top;
    }

    .invoice-box table tr td:nth-child(2) {
        text-align: right;
    }

    .invoice-box table tr.top table td {
        padding-bottom: 20px;
    }

    .invoice-box table tr.top table td.title {
        font-size: 45px;
        line-height: 45px;
        color: #333;
    }

    .invoice-box table tr.information table td {
        padding-bottom: 40px;
    }

    .invoice-box table tr.heading td {
        background: #eee;
        border-bottom: 1px solid #ddd;
        font-weight: bold;
    }

    .invoice-box table tr.details td {
        padding-bottom: 20px;
    }

    .invoice-box table tr.item td{
        border-bottom: 1px solid #eee;
    }

    .invoice-box table tr.item.last td {
        border-bottom: none;
    }

    .invoice-box table tr.total td:nth-child(2) {
        border-top: 2px solid #eee;
        font-weight: bold;
    }

    @media only screen and (max-width: 600px) {
        .invoice-box table tr.top table td {
            width: 100%;
            display: block;
            text-align: center;
        }

        .invoice-box table tr.information table td {
            width: 100%;
            display: block;
            text-align: center;
        }
    }

    /\*\* RTL \*\*/
    .rtl {
        direction: rtl;
        font-family: Tahoma, 'Helvetica Neue', 'Helvetica', Helvetica, Arial, sans-serif;
    }

    .rtl table {
        text-align: right;
    }

    .rtl table tr td:nth-child(2) {
        text-align: left;
    }
    </style>
</head>

<body>
    <div class="invoice-box">
        <table cellpadding="0" cellspacing="0">
            <tr class="top">
                <td colspan="2">
                    <table>
                        <tr>
                            <td class="title">
                                <img src="https://s2-cdn.greenhouse.io/external\_greenhouse\_job\_boards/logos/400/817/300/resized/Airkit-Symbol-RGB-Gradient.png?1568405564" style="width:30%; max-width:300px;">
                            </td>
                            <td>
                              <br>
                                Avengers, Inc.<br>
                                890 Fifth Avenue<br>
                                Manhattan, NY 10021
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
            <tr class="information">
                <td colspan="2">
                    <table>
                      <hr>
                        <tr>
                            <td>
                                Super Person<br>
                                John Doe<br>
                                john@email.com
                            </td>
                            <td>
                                Invoice #: AAC-023745<br>
                                Created: November 3, 2020<br>
                                Due: February 1, 2021
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>

            <tr class="heading">
                <td>
                    Payment Method
                </td>

                <td>
                    CC # (last 4 digits)
                </td>
            </tr>

            <tr class="details">
                <td>
                    Credit Card
                </td>

                <td>
                    1000
                </td>
            </tr>

            <tr class="heading">
                <td>
                    Item
                </td>

                <td>
                    Price
                </td>
            </tr>

            <tr class="item">
                <td>
                    Hulk foam fists
                </td>

                <td>
                    $30.00
                </td>
            </tr>

            <tr class="item">
                <td>
                    Avengers Subscription (1 year)
                </td>

                <td>
                    $75.00
                </td>
            </tr>

            <tr class="item last">
                <td>
                    Captain America shield
                </td>

                <td>
                    $50.00
                </td>
            </tr>

            <tr class="total">
                <td></td>

                <td>
                   Total: $155.00
                </td>
            </tr>
          </table>
          <br><br>
          <table>
            <tr>
                  <td>Signature: </td>
            </tr>
            <td>
            <tr><img width="300" height="100" src="https://www.airkit.com/wp-content/uploads/2020/09/airkit.logo\_.svg" /></td></tr>
            <tr>
              <td>Print Name: <b>My Name</b></td>
            </tr>
        </table>
    </div>
</body>
</html>
```