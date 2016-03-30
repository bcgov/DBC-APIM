#BC Route Planner
#Developer Guide
This guide is aimed at developers and web masters that would like to incorporate the BC Route Planner into their applications and websites.
<br>
##Introduction
The BC Route Planner REST API lets you integrate basic routing between BC locations into your own applications. This document defines aspects of the REST API that are not covered in the [Swagger definition](https://raw.githubusercontent.com/bcgov/DBC-APIM/master/api-specs/router/router.json). You can explore the API in the [API Console](http://apps.gov.bc.ca/pub/api-explorer/?url=https://raw.githubusercontent.com/bcgov/DBC-APIM/master/api-specs/router/router.json) . 
<br>

Your application can store router results or display them on any web map because all result data is copyright Province of British Columbia.  

##API Key
Use of the BC Route Planner REST API is currently restricted to government applications. If you are working on a government application that needs routing, please please contact DataBC for an API key.


##Distance Resource
The distance resource represents the length and duration of the shortest or fastest route between given points. Here are some examples:

##Route Resource
The route resource represents the shortest or fastest route between given points and the length and duration of that route. Here are some examples:

##Directions Resource
The directions resource represents the turn-by-turn directions, shortest or fastest route between given points and the length and duration of that route. Here are some examples:



###Resource representations in HTTP Responses
The addresses resource will return a document in the requested format and spatial reference system.  Documents in formats that support a header record (e.g., XHTML, KML, GEOJSON, GEOJSONP, GML) will contain a single About Query representation describing the query and its execution, and one or more site address or intersection address representations. Documents in formats that don’t support a header record (e.g., CSV, SHPZ), will contain one or more site/intersection address representations.

####About Query Representation
Attribute Name |	Type
---------------------: | --- |
[searchTimestamp](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#searchTimestamp) | Datetime
[executionTime](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#executionTime) | Real
[version](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#version) | String 
[minScore](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#minScore)  | Integer 
[maxResults](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#maxResults) | Integer 
[echo](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#echo)  | Boolean
[interpolation](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#interpolation)  |	String 
[outputSRS](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#outputSRS) | Integer
[setBack](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#setBack) |Real 
 
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

####Intersection Address Representation
Attribute Name |	Type
---------------------: | ---
[fullAddress](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#fullAddress) |	String
[intersectionName](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#intersectionName) |	String
[localityName](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#localityName) |	String
[provinceCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#provinceCode]) |	String
[score](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#score) |	Integer
[matchPrecision](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#matchPrecision) |	String
[precisionPoints](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#precisionPoints) |	Integer
[provinceCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#provinceCode) |	String
[matchPrecision](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#matchPrecision) |	String
[precisionPoints](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#precisionPoints) |	Integer
[faults](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#faults) |	String
[intersectionID](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#intersectionID) |	String
[degree](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#degree) |	String



##Occupant/addresses Resource
The occupants/addresses resource is similar to the addresses resource. Its response will include an About Query representation plus one site representation and occupant representation for each address matched.

####Occupant Representation
Attribute Name |	Type
---------------------: | ---
[occupantName](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#occupantName) |	string
[occupantID](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#occupantID) |	string
[occupantAliasAddress](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#occupantAliasAddress) |	string
[occupantDescription](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#occupantDescription) |	string
[contactEmail](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#contactEmail) |	string
[contactPhone](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#contactPhone) |	string
[contactFax](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#contactFax) |	string
[websiteUrl](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#websiteUrl) |	string
[imageUrl](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#imageUrl) |	string
[keywords](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#keywords) |	string
[businessCategoryClass](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#businessCategoryClass) |	string
[businessCategoryDescription](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#businessCategoryDescription) |	string
[naicsCode](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#naicsCode) |	string
[dateOccupantUpdated](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#dateOccupantUpdated) |	string
[dateOccupantAdded](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#dateOccupantAdded) |	string
[custodianId](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#custodianId) |	string
[sourceDataId](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#sourceDataId) |	string
