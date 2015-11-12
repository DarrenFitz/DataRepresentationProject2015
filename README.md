# Data Representation and Querying Project 2015
## Galway City Public Sports Facilities.
### By Darren Fitzpatrick - G00311853

## Introduction
This project provides the design and documentation for the dataset "Galway City puplic Sports Facilities" which is available at [data.gov.ie](http://data.gov.ie)

The **Galway City Public Sports Facilities** Dataset provides the user with all the information about all the sport facilities in the Galway region. The API would be very beneficial for tourists interested in sports, or the active youths in the area. The API has the type and name of pitch and also could also utilise Sat Nav as the the Dataset includes the coordinates.

## About the data
This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [*Galway City Public Sports Facilities*](https://data.gov.ie/dataset/galway-city-public-sports-facilities/resource/2db7c358-4ec1-4cfb-9456-d935cc0157aa).
The CSV file contains 47 rows, the first being a header row with the names of each field.

Each entry has 12 columns with headings as folows:

| Headings       | Description                                                 | Example        |
| -------------- |:-----------------------------------------------------------:|:--------------:|
|X Coordinate    | Refers to the Longitude or how far east the location is.    | -9.134152048   |
|Y Coordinate    | Refers to the Latitude or how far north the location is.    | 53.26441536    |
|Object ID       | The unique ID given to each pitch.                          | 1              |
|Number          | The number assigned to each pitch.                          | a01            |
|Type            | Refers to what kind of pitch it is.                         | G.A.A Pitch    |
|Name            | The name of the pitch.                                      | Cappagh Park   |
|Lat             | Latitude coordinate of the pitch.                           | 53.264         |
|Long            | Longitude coordinate of the pitch.                          | -9.134         |
|EastITM         | Easterly Irish Transverse Mercator (ITM) co-ordinate.       | 524337.1       |
|NorthITM        | Westerly Irish Transverse Mercator (ITM) co-ordinate.       | 724385.8       |
|EastIG          | East Irish Grid Reference number.                           | 124370         |
|NorthIG         | North Irish Grid Reference number.                          | 224356.4       |

Note: X and Y co-ordinates are the same as Lat and Long values except more precise.

## HTTP Methods 
Method | Definitions
|---------- |-------------------------------------------------|
|**GET**    | Retrieve resource from server using a given URI |   
|**HEAD**   | Like GET, but retreives head only               |
|**POST**   | Send information as block of data to server     | 
|**PUT**    | Replaces data at the URI to the request data    | 
|**DELETE** | Delete the data at the URI                      |

## Using HTTP Methods
### List of Parks

You can use the HTTP GET method to display all of the facilities.
An appropriate URL for such a request would look like this.

*http://galwayfacilities.com/facilities/all*

This would product al of the parks in JSON format.
### HTTP Response in json
```json
[
  {
    "X":-9.13415204770846,
    "Y":53.26441535713331,
    "OBJECTID":1,
    "NUMBER":"a01",
    "TYPE":"G.A.A. Pitch",
    "NAME":"Cappagh Park",
    "Lat":53.264,
    "Long":-9.134,
    "EastITM":524337.139,
    "NorthITM":724385.826,
    "EastIG":124370.044,
    "NorthIG":224356.434
  },
  { ... },
  { ... },
  { ... },
] 
```


