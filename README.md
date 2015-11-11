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
### Using the HTTP POST method:

If you wanted to list all Fire Brigade and Ambulance Callouts information use a URL similar to this:
*http://DublinfirebrigadeandambulancecalloutsAPI.com/callouts/all*

Saying "all" will return an array of *all* of the callouts, in **JSON** format like so:

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

There are thousands of fields in the Dataset I have chosen so if you want to display just a few fields or a certain number of fields you can add that number to a URL.

**For Example**

http://DublinfirebrigadeandambulancecalloutsAPI.com/callouts/9

This would return only the first 9 instances of the callouts from the Dataset.

## Using the HTTP GET method:
If you wanted to list all Fire Brigade and Ambulance Callouts information along with a certain field of preference within the Dataset use a URL similar to this:

*http://DublinfirebrigadeandambulancecalloutsAPI.com/callouts/?District_ID=SWORDS*

- "?" Starts the query string
- [District_ID] shows the "Field of preference" so it will **search** for the information in the specific column of the Dataset that you requested.
- =[SWORDS] shows the "Prefered Field info" so it will **respond** with the information in the Dataset from the specific column that you requested

This would return a list of all of the Ambulance or Fire Brigade callouts that there has been to "Swords" from the "District_ID" column in the Dataset.

**Extra Information**

If there was a space between the two words in the column that you are requesting information from you simply add "+" to the URL.8
For example:

If you wanted to get all of the callouts to the "CITY CENTRE" area within the "District_ID" column your URL would only need a slight change:

*http://DublinfirebrigadeandambulancecalloutsAPI.com/callouts/?District_ID=CITY+CENTRE*

As you can see, the "+" sign was added between City and Centre to denote a space.

The following would be output in **JSON** Format:

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
    "District_Id":"CITY CENTRE",
    "TOC": "00:16:48",
    "ORD": "00:19:33",
    "MOB": "00:20:52",
    "IA": "00:25:01",
    "LS": "00:35:44",
    "AH": "00:43:23",
    "MAV": "00:54:48",
    "CD": "00:54:57",
  }
 ]
```

etc until all of the fields in the "City Centre" are output.

##Search for multiple fields at once:

Easy! Just follow the same logic as the first example but add in "&" to add some extra fields!

*http://DublinfirebrigadeandambulancecalloutsAPI.com/callouts/?District_ID=CITY+CENTRE&Agency=DA*

This searches for the District_ID "City Centre" and also the Agency "DA" together!

The following would be output in **JSON** Format:

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
    "District_Id":"CITY CENTRE",
    "TOC": "00:16:48",
    "ORD": "00:19:33",
    "MOB": "00:20:52",
    "IA": "00:25:01",
    "LS": "00:35:44",
    "AH": "00:43:23",
    "MAV": "00:54:48",
    "CD": "00:54:57",
  }
 ]
```
etc until all of the fields in the "City Centre" are output that come from the agency "DA".

As you can see the fields output are fields with only "City Centre" as the "District_ID" and "DA" as the Agency.




