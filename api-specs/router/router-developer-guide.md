#BC Route Planner
#Developer Guide
This guide is aimed at developers and web masters that would like to incorporate the BC Route Planner into their applications and websites.
<br>
##Introduction
The BC Route Planner REST API lets you integrate basic routing between BC locations into your own applications. This document defines aspects of the REST API that are not covered in the [Swagger definition](https://raw.githubusercontent.com/bcgov/DBC-APIM/master/api-specs/router/router.json). You can explore the API in the [API Console](http://apps.gov.bc.ca/pub/api-explorer/?url=https://raw.githubusercontent.com/bcgov/DBC-APIM/master/api-specs/router/router.json). 
<br>

Your application can store router results or display them on any web map.

##API Key
Use of the BC Route Planner REST API is currently restricted to government. If you are working on a government application that needs routing, please email [DataBC](mailto:datacat@gov.bc.ca) for an API key. Be sure to include the name of the project and the business area responsible.


##Distance Resource
The distance resource represents the length and duration of the shortest or fastest route between given points. Here are some examples:

1. Length of shortest route in km and json between Duncan and Metchosin<br>https://router.api.gov.bc.ca/distance.json?routeDescription=shortest%20distance%20in%20km%20and%20json&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>
   
2. Length of shortest route in km and kml between Duncan and Metchosin<br>https://router.api.gov.bc.ca/distance.kml?routeDescription=shortest%20distance%20in%20km%20and%20kml&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>

3. Length of fastest route in miles and html between Duncan and Metchosin<br>https://router.api.gov.bc.ca/distance.html?routeDescription=fastest%20distance%20in%20km%20and%20html&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnit=mi&apikey=myapikey<br>

### HTTP Response

The distance resource will return the folling representation:

####distance representation
Attribute Name |	Type
---------------------: | --- |
[routeDescription](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeDescription) | String
[searchTimestamp](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#searchTimestamp) | Datetime
[executionTime](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#executionTime) | Real
[version](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#version) | String 
[disclaimer](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#disclaimer) | String
[privacyStatement](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#privacyStatement) | String
[srsCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#srsCode) | Integer
[criteria](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#criteria) | String
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of start/stop points(x,y)
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[distanceUnit](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distanceUnit) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String

##Route Resource
The route resource represents the shortest or fastest route between given points and the length and duration of that route. Here are some examples:

1. Shortest route in km and json between Duncan and Metchosin<br>https://router.api.gov.bc.ca/route.json?routeDescription=shortest%20route%20in%20km%20and%20json&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>
   
2. Shortest route in km and kml between Duncan and Metchosin<br>https://router.api.gov.bc.ca/route.kml?routeDescription=shortest%20route%20in%20km%20and%20kml&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>

3. Fastest route in miles and html between Duncan and Metchosin<br>https://router.api.gov.bc.ca/route.html?routeDescription=fastest%20route%20in%20km%20and%20html&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnit=mi&apikey=myapikey<br>

###HTTP response
The route resource will return the following representation:

####route representation
Attribute Name |	Type
---------------------: | --- |
[routeDescription](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#routeDescription) | String
[searchTimestamp](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#searchTimestamp) | Datetime
[executionTime](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#executionTime) | Real
[version](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#version) | String 
[disclaimer](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#disclaimer) | String
[privacyStatement](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#privacyStatement) | String
[srsCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#srsCode) | Integer
[criteria](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#criteria) | String
[points](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#points) | list of start/stop points(x,y)
[distance](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distance) | String
[distanceUnit](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#distanceUnit) | String
[time](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#time) | Integer
[timeText](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#timeText) | String
[route](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/router/glossary.md#route) | Polyline






##Directions Resource
The directions resource represents the turn-by-turn directions, shortest or fastest route between given points and the length and duration of that route. Here are some examples:

1. Directions and shortest route in km and json between Duncan and Metchosin<br>https://router.api.gov.bc.ca/directions.json?routeDescription=directions%20Cand%20Cshortest%20route%20in%20km%20and%20json&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>
   
2. Directions and shortest route in km and kml between Duncan and Metchosin<br>https://router.api.gov.bc.ca/directions.kml?routeDescription=directions%20Cand%20Cshortest%20route%20in%20km%20and%20kml&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnits=km&apikey=myapikey<br>

3. Directions and fastest route in miles and html between Duncan and Metchosin<br>https://router.api.gov.bc.ca/route.html?routeDescription=directions%20Cand%20Cfastest%20route%20in%20km%20and%20html&points=-123.707942%2C48.778691%2C-123.537850%2C48.382005&outputSRS=4326&criteria=shortest&distanceUnit=mi&apikey=myapikey<br>


####Response Properties
Attribute Name |	Type
---------------------: | --- |
[searchTimestamp](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#searchTimestamp) | Datetime
[executionTime](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#executionTime) | Real
[version](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#version) | String 
[outputSRS](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#outputSRS) | Integer

####Site Address Representation
Attribute Name |	Type
---------------------: | ---
[fullAddress](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#fullAddress) |	String
[score](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#score) |	integer
[matchPrecision](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#matchPrecision) |	String
[precisionPoints](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#matchPrecision) | integer
[faults](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#faults) | String
[siteName](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#siteName) | String
[unitDesignator](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#unitDesignator) | String
[unitNumber](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#unitNumber) | String
[unitNumberSuffix](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#unitNumberSuffix) | String
[civicNumber](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#civicNumber) | String
[civicNumberSuffix](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#civicNumberSuffix) | String
[streetName](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#streetName) | String
[streetType](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#streetType) | String
[isStreetTypePrefix](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#isStreetTypePrefix) | Boolean
[streetDirection](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#streetDirection) | String
[isStreetDirectionPrefix](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#isStreetDirectionPrefix) | Boolean
[streetQualifier](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#streetQualifier) | String
[locationName](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#locationName) | String
[provinceCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#provinceCode) |	String
[locationPositionalAccuracy](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#locationPositionalAccuracy) |	String
[locationDescriptor](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#locationDescriptor) |	String
[siteID](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#siteID) |	string
[blockID](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#blockID) |	String
[fullSiteDescriptor](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#fullSiteDescriptor) |	String
[narrativeLocation](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#narrativeLocation) |	String
[accessNotes](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#accessNotes) |	String
[siteStatus](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#siteStatus) |	String
[siteRetireDate](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#siteRetireDate) |	Date
[changeDate](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#changeDate) |	string
[isPrimary](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#isPrimary) |	string

