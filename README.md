# Galway City Playgrounds
## Data Representation and Querying Project
###Paul Dolan

## Introduction
This project provides the design and documentation for the dataset "Galway City Playgrounds" which can be found at [data.gov.ie](http://data.gov.ie)

The **Playgrounds in Galway City** Dataset contains information and the whereabouts of all of the public playgrounds that can be found in Galway City.

## Information about the Playgrounds in the Galway City Playgrounds dataset
The dataset that I have used was originally a .csv file however I transferred it to json using an online application which has made it easier to use. The dataset contains 15 entries. Every column has 17 columns which are as follows:
  
Heading | Meaning 
 ------|---------
"**OBJECTID**" | "An id for the playground",
"**PLAYGROUND**" | "The name given to the playground",
"**Location**" | "The location of the playground",
"**SURFACE**" | "What sort of ground surface the playground possesses",
"**PARKING**" | "Where is there parking for the playground",
"**OPENHRS**" | "Opening hours for the playground",
"**TOILETFACI**" | "Whether there is toilet facilities or not",
"**EQUIPMENT**" | "What sort of equipment the playground eg. Slides, monkey bars etc.",
"**Lat**" | "Latitude",
"**Long**" | "Longitude",
"**EastITM**" | "Irish Transverse Mercator (ITM) East value",
"**NorthITM**" | "Irish Transverse Mercator (ITM) North vaule",
"**EastIG**" | "East Irish Grid Reference number",
"**NorthIG**" | "North Irish Grid Reference number"

##
Below is a link to the Irish Transverse Mercator (ITM), otherwise known as the geographic coordinate system for Ireland and also the Irish Grid Reference System which is a system of geographic grid references commonly used in Ireland (both Northern Ireland and the Republic of Ireland).

*https://en.wikipedia.org/wiki/Irish_Transverse_Mercator*

*https://en.wikipedia.org/wiki/Irish_grid_reference_system*
 

I deleted the two columns which were of no use which was the X and Y coordinates as there is already a latitude and longitude included in the columns. However I also deleted the colums 'SPECIANNEE' as I didn't understand what it meant.


##Status Code
| Code | Description |    
|------|:--------|     
**200** | Ok | 
**202** | Accepted  |  
**400** | Bad Request | 
**404** | Not Found  |  
**405** | Method Not Allowed | 
**503** | Service Unavaiable |

## Example
>Here is my first entry from the "Galway City Playgrounds" dataset which is formatted in json which will show you how the columns are used.

    {
        "OBJECTID": "1",
        "PLAYGROUND": "Gleann Bhan Playground",
        "Location": "Ballybane, Galway",
        "SURFACE": "Rubber Wet-pour surface",
        "PARKING": "Within estate",
        "OPENHRS": "No restricted opening hours",
        "TOILETFACI": "No",
        "EQUIPMENT": " ",
        "Lat": "53.286",
        "Long": "-8.999",
        "EastITM": "533391.393",
        "NorthITM": "726687.764",
        "EastIG": "133426.244",
        "NorthIG": "226658.92"
    },


  
##HTTP Request Methods  
Method | Meanings
--------|--------------------------------
**GET** | Retrieve information from the server  
**HEAD** | Retrieve response header   
**POST** | Send data to the server       
**PUT** | Set the data at the URI to the request data   
**DELETE** | Delete the data at the URI

###Querying the Dataset  
You may query the dataset using the  HTTP rerequest methods and the URL. The response would be in a json format. 

###Example of querying the dataset
*http://galwayplaygrounds.ie/[PLAYGROUND]*   
###when you replace [PLAYGROUND] with the name of the playground:
*http://galwayplaygrounds.ie/mervuepublicparkplayground*   


###HTTP Requst by Object ID
GET *http://galwayplaygrounds.ie/mervuepublicparkplayground*   

###HTTP Response in json
   {

        "OBJECTID": "2",
        "PLAYGROUND": "Mervue Public Park Playground",
        "Location": "Mervue, Galway",
        "SURFACE": "Rubber Wet-pour surface",
        "PARKING": "Within estate",
        "OPENHRS": "No restricted opening hours",
        "TOILETFACI": "No",
        "EQUIPMENT": " ",
        "Lat": "53.283",
        "Long": "-9.018",
        "EastITM": "532120.521",
        "NorthITM": "726326.313",
        "EastIG": "132155.1",
        "NorthIG": "226297.384"
    },


## Accessing The Dataset
#### Receiving a list of all playgrounds in Galway City
You can receive a list of all the playgrounds in Galway City, using the HTTP POST method, and the following URL:

*http://galwayplaygrounds.ie/all*

Here we are using "all" after "/playgrounds/" which will return all of the playgrounds in Galway City

###HTTP Requst by Object ID
GET *http://galwayplaygrounds.ie/all*   

###HTTP Response in json

    {
        "OBJECTID": "3",
        "PLAYGROUND": "Lakeshore Drive Playground",
        "Location": "Renmore, Galway",
        "SURFACE": "Rubber Wet-pour surface",
        "PARKING": "Within estate",
        "OPENHRS": "No restricted opening hours",
        "TOILETFACI": "No",
        "EQUIPMENT": " ",
        "Lat": "53.277",
        "Long": "-9.028",
        "EastITM": "531413.082",
        "NorthITM": "725664.03",
        "EastIG": "131447.51",
        "NorthIG": "225634.955"
    },
    {...},
    {...},
    ...
  
### Accessing list of playgrounds using filters
You may request a list of playgrounds using a filter eg. All playgrounds with parking etc using the HTTP GET method.
Here is a URL example of the address you would use to achieve this.

*http://galwayplaygrounds.ie/playgrounds/?[filter]=[parameter]*

We now replace [filter] with a dataset field eg. Location, surface etc.

Then replace [parameter] with what you are looking for.

**Example One**

*http://galwayplaygrounds.ie/playgrounds/?surface=RubberWet-poursurface/*

This would return all of the playgrounds that provide a rubber wet-pour surface.

If there isn't any playground with that surface, an empty array is returned.

**Example Two**

*http://galwayplaygrounds.ie/playgrounds/?parking=withinestate*

This would return all of the playgrounds that have parking within the estate of the playground.

If there isn't any parking within the estate, an empty array is returned.

**Example Three**

*http://galwayplaygrounds.ie/playgrounds/?TOILETFACI=yes*

This would return all of the playgrounds that have toilet facilities within the surrounding area of the playground.

#### A list of playgrounds closest to your current location

Perhaps you wanted to find the playgrounds closest to your current location. All you have to do is use the users longitude and latitude, with a POST method, using the following URL:

*http://galwayplaygrounds.ie/playgrounds/closest-long-lat/*

This will return all the playgrounds starting with the playground that is closest to the longitude and latitude coordinates provided
