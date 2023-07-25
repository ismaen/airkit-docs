Working with dates and times is a notoriously difficult problem, the most famous incantation being Y2K. Airkit provides a comprehensive system to work with dates and times for this precise reason. There are three data types to familiarize yourself with, the [Datetime](https://support.airkit.com/reference/the-datetime-variable-data-type), the [Date](https://support.airkit.com/reference/the-date-variable-data-type), and the [Time](https://support.airkit.com/reference/the-time-variable-data-type) types. The best way to think of these is by analogy. A Datetime is a specific time marked on your calendar. A Date is a particular day's square on your calendar. A Time is a particular configuration of your clock.


If you would like to find the current Datetime you can use the [NOW](https://support.airkit.com/reference/now) function.



```javascript Airscript
NOW()
```

Other ways to create a date/time are to use the functions [DATETIME](https://support.airkit.com/reference/datetime), [DATE](https://support.airkit.com/reference/date), and [TIME](https://support.airkit.com/reference/time). Using January 9th, 2007 9:41 AM as an example Datetime**:**



```javascript Airscript
DATETIME(DATE(2007, 1, 9), TIME(9, 41, 0), "America/Los_Angeles")  
DATE(2007, 1, 9)  
TIME(9, 41, 0)
```

To retrieve the year of our example Date use the [YEAR](https://support.airkit.com/reference/year) function:



```javascript Airscript
YEAR(example_date)
```

The [YEAR](https://support.airkit.com/reference/year) function can also be used to retrieve the year from our example Datetime:



```javascript Airscript
YEAR(example_datetime)
```

Use the [DATE_FROM_DATETIME](https://support.airkit.com/reference/date_from_datetime) and the [TIME_FROM_DATETIME](https://support.airkit.com/reference/time_from_datetime) functions to convert a Datetime to a **Date** or **Time** respectively:



```javascript Airscript
DATE_FROM_DATETIME(example_datetime)  
TIME_FROM_DATETIME(example_datetime)
```

The following functions can be used to retrieve different parts of Datetimes, Dates, and Times




| Function Name | Description |
| --- | --- |
| [DATE_FROM_DATETIME](https://support.airkit.com/reference/date_from_datetime) | Returns the **date** portion of a **Datetime.** |
| [TIME_FROM_DATETIME](https://support.airkit.com/reference/time_from_datetime) | Returns the **time** portion of a **Datetime.** |
| [YEAR](https://support.airkit.com/reference/year) | Returns the **year** of a **Datetime** or **Date** |
| [MONTH](https://support.airkit.com/reference/month) | Returns the **month** of a **Datetime** or **Date** |
| [DAY](https://support.airkit.com/reference/day) | Returns the **day** of a **Datetime** or **Date** |
| [HOUR](https://support.airkit.com/reference/hour) | Returns the **hour** of a **Datetime** or **Time** |
| [MINUTE](https://support.airkit.com/reference/minute) | Returns the **minute** of a **Datetime** or **Time** |
| [SECOND](https://support.airkit.com/reference/second) | Returns the **second** of a **Datetime** or **Time** |


Formatting
----------


The [FORMAT_DATETIME](https://support.airkit.com/reference/format_datetime), [FORMAT_DATE](https://support.airkit.com/reference/format_date), and [FORMAT_TIME](https://support.airkit.com/reference/format_time) functions allow you to create a String from a Datetime, Date, or Time. Use these functions when you would like to display a **Datetime**, **Date**, or **Time** to a user so that Airkit can format it correctly according to the user's locale and timezone. For example, to display our example Datetime as **January 9, 2007 9:41 AM PST**:



```javascript Airscript
FORMAT_DATETIME(example_datetime, "MMMM do, YYYY h:mm A")
```

or just the time as **9:41 AM**:



```javascript Airscript
FORMAT_DATETIME(example_datetime, "h:mm A")
```

Modifying
---------


### Modifying with a Specific Value


If you want to change a particular portion of a Datetime, there are several functions that will allow you to do so. For example, if you wanted to change the year of our example Datetime from **2007** to **2010**, you would use the [UPDATE_YEAR](https://support.airkit.com/reference/update_year) function to create a new Datetime by changing only the year:



```javascript Airscript
UPDATE_YEAR(example_datetime, 2010)
```

This function works equally well on Dates:



```javascript Airscript
UPDATE_YEAR(example_datetime, 2010)
```

If you wanted to update the calendar date of the Datetime, you can use the [UPDATE_DATE](https://support.airkit.com/reference/update_date) function to create a new Datetime, with a new calendar date, but the same time:



```javascript Airscript
UPDATE_DATE(example_datetime, DATE(2010, 4, 3))
```

**Datetimes**, **Dates**, and **Times** can be modified using the following functions




| Function Name | Description |
| --- | --- |
| [UPDATE_DATE](https://support.airkit.com/reference/update_date) | Changes the **date** portion of a **Datetime.** |
| [UPDATE_TIME](https://support.airkit.com/reference/update_time) | Changes the **time** portion of a **Datetime.** |
| [UPDATE_TIMEZONE](https://support.airkit.com/reference/update_timezone) | Changes the **timezone** of a **Datetime.** |
| [UPDATE_YEAR](https://support.airkit.com/reference/update_year) | Changes the **year** of a **Datetime** or **Date** |
| [UPDATE_MONTH](https://support.airkit.com/reference/update_month) | Changes the **month** of a **Datetime** or **Date** |
| [UPDATE_DAY](https://support.airkit.com/reference/update_day) | Changes the **day** of a **Datetime** or **Date** |
| [UPDATE_HOUR](https://support.airkit.com/reference/update_hour) | Changes the **hour** of a **Datetime** or **Time** |
| [UPDATE_MINUTE](https://support.airkit.com/reference/update_minute) | Changes the **minute** of a **Datetime** or **Time** |
| [UPDATE_SECOND](https://support.airkit.com/reference/update_second) | Changes the **second** of a **Datetime** or **Time** |
| [UPDATE_MILLISECOND](https://support.airkit.com/reference/update_millisecond) | Changes the **millisecond** of a **Datetime** or **Time** |


### Modifying with a Relative Value


The [ADD_TO_DATETIME](https://support.airkit.com/reference/add_to_datetime) and [SUBTRACT_FROM_DATETIME](https://support.airkit.com/reference/subtract_from_datetime) functions allow you to create a new date by adding or removing time units. You could add six months, or 169 days to our example date**:**



```javascript Airscript
ADD_TO_DATETIME(example_datetime, 6, "M")  
ADD_TO_DATETIME(example_datetime, 169, "d")
```

Timestamps
----------


When interfacing with external systems, you'll often encounter Datetimes that are represented either as a Number or a String.


### **Datetime as a Number**


An Epoch timestamp is a Number representing the number of seconds (or milliseconds) that have elapsed since January 1st, 1970. For example the timestamp in milliseconds for January 9ith, 2007 is **1168364460000**. When you encounter a Datetime in this format look to the [DATETIME_FROM_TIMESTAMP](https://support.airkit.com/reference/datetime_from_timestamp) function which turns an Epoch timestamp measured in milliseconds into a proper Datetime.



```javascript Airscript
DATETIME_FROM_TIMESTAMP(1168364460000)
```

To go in the other direction look no further than the [TIMESTAMP_FROM_DATETIME](https://support.airkit.com/reference/timestamp_from_datetime) function.



```javascript Airscript
TIMESTAMP_FROM_DATETIME(example_datetime)
```

If your particular timestamp looks like it is missing three zeros than the previous example, you are likely working with timestamps in seconds, provide second parameter **"s"**



```javascript Airscript
DATETIME_FROM_TIMESTAMP(1168364460, "s")  
TIMESTAMP_FROM_DATETIME(example_datetime, "s")
```

### **Datetime as a String**


The other commonly used timestamp type is a string with the format **"YYYY-MM-DDTHH:mm:ssZ"**. To convert between a timestamp of this format and a Datetime use the [DATETIME_FROM_FORMAT](https://support.airkit.com/reference/datetime_from_format) and [FORMAT_DATETIME](https://support.airkit.com/reference/format_datetime) functions.



```javascript Airscript
DATETIME_FROM_FORMAT("2007-01-09T09:41:00Z")  
FORMAT_DATETIME(example_datetime)
```

Timezones
---------


Note that one of our previous examples reproduced below included a timezone:



```javascript Airscript
DATETIME(DATE(2007, 1, 9), TIME(9, 41, 0), "America/Los_Angeles")
```

This is important because, in addition to a Date and a Time, Datetimes also have an associated timezone.


Relevant Functions
------------------


* [NOW](https://support.airkit.com/reference/now)
* [TODAY](https://support.airkit.com/reference/today)
* [DATETIME](https://support.airkit.com/reference/datetime)
* [DATE](https://support.airkit.com/reference/date)
* [TIME](https://support.airkit.com/reference/time)
* [DATE_FROM_DATETIME](https://support.airkit.com/reference/date_from_datetime)
* [TIME_FROM_DATETIME](https://support.airkit.com/reference/time_from_datetime)
* [YEAR](https://support.airkit.com/reference/year)
* [MONTH](https://support.airkit.com/reference/month)
* [DAY](https://support.airkit.com/reference/day)
* [HOUR](https://support.airkit.com/reference/hour)
* [MINUTE](https://support.airkit.com/reference/minute)
* [SECOND](https://support.airkit.com/reference/second)
* [FORMAT_DATE](https://support.airkit.com/reference/format_date)
* [FORMAT_TIME](https://support.airkit.com/reference/format_time)
* [UPDATE_DATE](https://support.airkit.com/reference/update_date)
* [UPDATE_TIME](https://support.airkit.com/reference/update_time)
* [UPDATE_TIMEZONE](https://support.airkit.com/reference/update_timezone)
* [UPDATE_YEAR](https://support.airkit.com/reference/update_year)
* [UPDATE_MONTH](https://support.airkit.com/reference/update_month)
* [UPDATE_DAY](https://support.airkit.com/reference/update_day)
* [UPDATE_HOUR](https://support.airkit.com/reference/update_hour)
* [UPDATE_MINUTE](https://support.airkit.com/reference/update_minute)
* <UPDATE_SECOND>
* [UPDATE_MILLISECOND](https://support.airkit.com/reference/update_millisecond)
* [ADD_TO_DATETIME](https://support.airkit.com/reference/add_to_datetime)
* [SUBTRACT_FROM_DATETIME](https://support.airkit.com/reference/subtract_from_datetime)
* [DATE_DELTA](https://support.airkit.com/reference/date_delta)
* [TIME_DELTA](https://support.airkit.com/reference/time_delta)
* [DATETIME_FROM_TIMESTAMP](https://support.airkit.com/reference/datetime_from_timestamp)
* [TIMESTAMP_FROM_DATETIME](https://support.airkit.com/reference/timestamp_from_datetime)
* [DATETIME_FROM_FORMAT](https://support.airkit.com/reference/datetime_from_format)
* [DATE_FROM_FORMAT](https://support.airkit.com/reference/date_from_format)
* [TIME_FROM_FORMAT](https://support.airkit.com/reference/time_from_format)