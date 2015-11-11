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
Below is a link to the Irish Transverse Mercator (ITM), otherwise known as the geographic coordinate system for Ireland
*https://en.wikipedia.org/wiki/Irish_Transverse_Mercator*
 

I deleted the two columns which were of no use which was the X and Y coordinates as there is already a latitude and longitude included in the columns. However I also deleted the colums 'SPECIANNEE' as I didn't understand what it meant.

## Example
Here is my first entry from the "Galway City Playgrounds" dataset which is formatted in json which will show you how the columns are used.

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

###Example
*http://galway.ie/playgrounds/[OBJECTID]*   
###The above would return:
*http://galway.ie/playgrounds/2*   


###HTTP Requst by Object ID
GET *http://galway.ie/playgrounds/2*   

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





