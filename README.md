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
|Method     | Definitions                                     |
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

This would product all of the facilities in JSON format.
**HTTP Response in json**
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
To get all the names of the facilities using the GET method might have a URl as follows.
This URL returns back all of the names as opposed to all of the headings.

*http://galwayfacilities.com/facilities/names*

| Heading | Description|
| ------------- |:--------------------:|
| Name          | The facilities name. |

**HTTP Response in json**
```JSON
[ {"Name": "Cappagh Park", 
   "Name": "McGraths Field",
   "Name": "McGraths Field 1",
   "Name": "McGraths Field 2",
   "Name": "Westside Sports",
   "Name": "Laurel Park"}]
```

### Location of the Facilities 
To get a specific facility we use the http GET method to control the dataset. We could use a id to get our designated object (id =5). This method returns all of the information from the fifth row. We can implement the already assigned ID into the URL like this: 

*http://galwayfacilities.com/facilities/id=5*

| Heading | Description|
| ------------- |:--------------------:|
| Object ID     | Unique object number.|

**HTTP Response in json**
```JSON
[ {
    "X":-9.111071048579548,
    "Y":53.26358136885726,
    "OBJECTID":5,
    "NUMBER":"a05",
    "TYPE":"G.A.A. Pitch",
    "NAME":"McGraths Field",
    "Lat":53.264,
    "Long":-9.111,
    "EastITM":525875.447,
    "NorthITM":724268.851,
    "EastIG":125908.684,
    "NorthIG":224239.443
  }]
```

 
To get the location of the facility we use the http GET method. For the URL we can get any of the named facilities with a URL like this:

*http://galwayfacilities.com/facilities/location/[NAME]*

The [NAME] is replace with a name of a facility in the dataset. And it will return the longitude and latitude of the facility e.g Westside Sports.

*http://galwayfacilities.com/facilities/location/Westside_Sports*

| Heading | Description|
|-----------|:---------------------:|
| Latitude  | Facility co-ordinates |
| Longitude | Facility co-ordinates |

**HTTP Response in json**
```JSON
[ {
    "Lat":53.275,
    "Long":-9.081,
  },
  { ... },
  { ... }
  ]
```
### Using PUT method to add data to dataset
Here is an example of how we use PUT to update a record.
``` http://galwayfacilities.com/facilities/new ```

**Request Body Example**
```
  - PUT   /galwayfacilities/new.html HTTP/1.1
  - Host: galwayfacilities.com
  - OBJECTID="5"&NUMBER="a05"&TYPE="G.A.A.Pitch"&NAME="McGrathsFiels"&LAT="53.262"&LONG="-9.134"
  
```
### Using DELETE method to remove data from dataset
To delete something from a dataset you must us ethe DELETE method.
To pick a column to be deleted whe use a unique identifier such as "OBJECT ID".
You use DELETE method at following URL:

``` http://galwayfacilities.com/facilities/delete/id=6 ```

**Response Example**
```
      HTTP/1.1 200 OK
      "URL DELETED"
...
```


