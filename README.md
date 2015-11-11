# data-projectcf
## Data Representation and Querying Project 2015
### Claire Finn
## Dublin Fire Brigade and Ambulance Call Outs API

## About the data
This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [*Fire Brigade and Ambulance Call Outs*](https://data.gov.ie/dataset/fire-brigade-and-ambulance-call-outs).
The CSV file contains 9523 rows, the first being a header row with the names of each field.
There are twelve values on each line, which are as follows:

Field| Description
------------ | -------------
Date| The date the incident happened.
Agency| Company that provides the service
Station Area| Postcode
District_Id | Area incident happened
TOC| The time the call is received in the control centre
ORD| The time the vehicle is ordered, i.e., mobilised to the incident by a control operator
MOB| The time at which the vehicle is mobile to incident (the vehicle has started to move) 
IA|  The time the vehicle is in attendance (the vehicle is stopped at the incident) 
LS|  The time the vehicle is in attendance (the vehicle is stopped at the incident) 
AH|The time at hospital (ambulance has arrived at hospital) 
MAV|The time at which the vehicle is mobile and available (vehicle heading back to station)
CD|The time at which the vehicle is closing down (back at station, vehicle radio is being shut down)

## JSON Format
The Dataset, taking the first row for example, looks like this in JSON Format:

```json
[
{
    "Date":01-01-2011,
    "Agency":"DA",
    "Station Area":"D10",
    "District_Id":"City Centre",
    "TOC": "00:05:16",
    "ORD": "00:07:33",
    "MOB": "00:07:50",
    "IA": "00:09:12",
    "LS": ,
    "AH": "00:21:19",
    "MAV": "00:37:53",
    "CD": "00:41:44",
  }
  ]
```
## HTTP Responses on my Dataset
### If you wanted to list all Fire Brigade and Ambulance Callouts information using the HTTP POST method:

Use a URL similar to this:
*http:// DublinfirebrigadeandambulancecalloutsAPI.com/callouts/all*

Saying "all" will return an array of *all* of the callouts, in JSON format like so:

```json
[
 {
    "Date":01-01-2011,
    "Agency":"DA",
    "Station Area":"D10",
    "District_Id":"CITY CENTRE",
    "TOC": "00:05:16",
    "ORD": "00:07:33",
    "MOB": "00:07:50",
    "IA": "00:09:12",
    "LS": "",
    "AH": "00:21:19",
    "MAV": "00:37:53",
    "CD": "00:41:44",
  }
  {
    "Date":01-01-2011,
    "Agency":"DA",
    "Station Area":"D10",
    "District_Id":"SAINT STEPHENS GREEN",
    "TOC": "00:05:18",
    "ORD": "",
    "MOB": "",
    "IA": "",
    "LS": "",
    "AH": "",
    "MAV": "",
    "CD": "00:09:47",
  }
]
```
*Etc* Until all of the information in the table is displayed.
