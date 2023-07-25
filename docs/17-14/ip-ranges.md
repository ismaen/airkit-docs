Using the endpoint <https://ip-ranges.airkit.com/>, users can get Airkit's IP egress ranges. This means that when Airkit is making an external connection or API call, this is where they are coming from.


When working with the IP ranges, it is best practice to rely on the below endpoint and not hard code the ranges, as they are subject to change.


#### **GET**



```
https://ip-ranges.airkit.com/
```

#### **Response**


200 OK


#### **Example Response**



```json Airscript
{
    "egress": [
        "54.70.193.241/32",
        "44.230.80.213/32",
        "100.20.135.25/32",
        "13.211.113.145/32",
        "3.105.112.126/32",
        "3.126.58.60/32",
        "3.126.39.166/32"
    ]
}
```