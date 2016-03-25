#BC Physical Address Geocoder
#Developer Guide
This guide is aimed at developers and web masters that would like to incorporate the Physical Address Geocoder into their applications and websites.
<br>
##Introduction
The BC Physical Address Online Geocoder REST API lets you integrate real-time standardization, validation, and geocoding of physical addresses into your own applications. This document defines the REST API. 
To simplify integration of the online geocoder into your client web application, you can use the Javascript API located at:
http://apps.gov.bc.ca/pub/geocoder/js/geocode.js 
<br>
##API Changes in v2.0
1.	A site can now have one or more public or related business occupants. Here is an example:
VICTORIA LAW COURTS -- 850 Burdett Ave, Victoria, BC
Resources have been added to support validating, geocoding, and finding occupants nearby but only courts of law and some hospitals have been loaded. Expect a lot more occupants in the near future. Here are some example requests:<br><br>
http://apps.gov.bc.ca/pub/geocoder/occupants/addresses.geojson?tags=courts&addressString=victoria%20law%20courts%20--%20<br><br>
http://apps.gov.bc.ca/pub/geocoder/occupants/nearest.geojson?point=-123.7064038,48.8498537&tags=courts<br><br> 
http://apps.gov.bc.ca/pub/geocoder/occupants/near.geojson?point=-123.7064038,48.8498537&tags=courts&maxResults=3<br><br>
2.	The documentation has been updated.

##Resource Overview
The Online Geocoder offers resources for validating and geocoding an address (including public and related business occupants); finding a given site, intersection, and occupant; and finding sites, intersections, and occupants near a point or within an area. 
The current baseUrl for the online geocoder is:<br>
http://apps.gov.bc.ca/pub/geocoder<br><br>
The baseUrl for the online geocoder under the HTTP Secure protocol is:<br> 
https://apps.gov.bc.ca/pub/geocoder

##Addresses Resource
The addresses resource represents all addresses in the geocoder. A request on this resource to find a query address will return one or more matching addresses that are standardized and geocoded (i.e., given a point location on the earth). 

A query address can be specified in two different ways:

1.	A single address string containing all elements of an address as in:<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.geojson?addressString=525%20superior%20st,%20victoria,%20bc<br><br> 
2.	Individual address elements as in:<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.geojson?civicNumber=525&streetName=superior&streetType=st&localityName=victoria&provinceCode=BC

Here are some more example geocoder requests:

1.	Geocode 456 Gorge Rd E, Victoria, BC<br> 
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?addressString=456%20Gorge%20Rd%20e%20victoria%20bc<br><br>
2.	Geocode 7-955 13th Ave, Valemount, BC<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?addressString=7-955%2013th%20ave,%20Valemount,bc<br><br> 
3.	Geocode the intersection at Johnson and Government<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?addressString=johnson%20and%20government<br><br> 
4.	Geocode 5671 Malibu Terrace, Nanaimo, BC and return results in GEOJSON and BC Albers projection<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.geojson?outputSRS=3005&addressString=5671%20malibu%20terrace%20nanaimo%20bc<br><br>
5.	Geocode 5670 Malibu Terrace, Nanaimo and return the location along the road centreline for using in routing<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.kml?locationDescriptor=routingPoint&addressString=5670%20malibu%20terrace%20nanaimo%20bc<br><br>
6.	Geocode 5670 Malibu Terrace, Nanaimo and return accessPoint set back four metres from the curb towards the inside of the property. Note that only accessPoints can be set back<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.kml?locationDescriptor=accessPoint&setBack=4&addressString=5670%20malibu%20terrace%20nanaimo%20bc<br><br>  
7.	Geocode 5671 Malibu Terrace, Nanaimo, BC without interpolation. In other words, if the geocoder doesn’t have a site with a civic number of 5671, it will fail instead of looking for an address range that contains 5671<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?interpolation=none&addressString=5671%20malibu%20terrace%20nanaimo%20bc<br><br>
8.	Geocode 200 Gorge Rd W, Saanich, BC and limit results to Victoria. It will return 200 Gorge Rd E, Victoria, BC since Gorge Rd E is in Victoria<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?localities=victoria&addressString=200%20gorge%20rd%20w%20saanich%20bc<br><br> 
9.	Geocode 1434 Graham St, Kelowna, BC and limit results to ten matches within the greater Kelowna area<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?&bbox=-119.8965522070019%2C49.70546831817266%2C-119.2157397287486%2C50.06954472056336&addressString=1434%20Graham%20St%2C%20Kelowna%2C%20BC&maxResults=10<br><br>
10.	Geocode 1434 Graham St, Kelowna, BC and limit results to ten street-level matches<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?&addressString=1434%20Graham%20St%2C%20Kelowna%2C%20BC%20&matchPrecision=street&maxResults=10<br><br> 
11.	Extrapolate the known location of 12 Bushby St from a parcelPoint to get an accessPoint<br> 
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?setBack=0&minScore=1&maxResults=1&maxDistance=0&interpolation=adaptive&echo=true&outputSRS=4326&addressString=12%20bushby%20st%20victoria%20bc&locationDescriptor=any&extrapolate=true&parcelPoint=-123.349174,2048.407134<br><br> 
12.	Find the nearest courthouse to a given point<br>
http://apps.gov.bc.ca/pub/geocoder/occupants/nearest.geojson?point=-123.7064038,48.8498537&tags=courts<br><br>
<br>

###Resource representations in HTTP Responses
This resource will return a document in the requested format and spatial reference system.  Documents in formats that support a header record (e.g., XHTML, KML, GEOJSON, GEOJSONP, GML) will contain a single About Query record describing the query and its execution, and one or more site address or intersection address records. Documents in formats that don’t support a header record (e.g., CSV, SHPZ), will contain one or more site/intersection address records.

Here we define the attributes of the different record types that are returned in a response document. For the precise structure of a given document format, geocode an address using the online geocoder in the desired format and examine the result.
 
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

###Intersection Address Representation
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
[degree](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#) |	String

SiteAndIntersection Address Record
Site/Intersection Address Attribute	Type	Description

[](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#) |	string
[](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#) |	string
[](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#) |	string
[](https://github.com/bcgov/DBC-APIM/blob/master/api-specs/geocoder/glossary.md#) |	string



fullAddress	String	Civic, non-civic address, or intersection address in Single-Line Address Format (see last section of this document)
intersectionName	String	The street name, type, and direction of all streets that meet at a given intersection. Here are some examples:
•	Douglas St and Gorge Rd E and Hillside Ave
•	48th Ave W and Marine Dr SW
score	Integer	Match score (between 0 and 100)
matchPrecision	String	The level of precision of an address match. Here are all the  levels from the most precise to least precise:
•	civicNumber – the civic number matched
•	block – the civic number falls within a known block range
•	intersection - the intersection name matched
•	street – the street name, street direction, and street type matched
•	locality – the locality matched
•	province – no match
precisionPoints	Integer	Points given for matchPrecision
faults	String	The list of faults found with a given address match. Each fault contains the nature of the fault, the address property affected, and the fault penalty.
siteName	String	A string containing the name of the building, facility, or institution (e.g., Duck Building, Casa Del Mar, Crystal Garden, Bluebird House). A business name should only be used if it is permanently affixed to the site and the site has no other, more generic name. If a site is a unit within a complex, it may have a sitename in addition to a unitNumber and unitSuffix. siteName is optional for civic addresses but required for non-civic addresses.
unitDesignator	String	The type of unit within a house or building. Valid values are APT, BLDG, BSMT, FLR, LOBBY, LWR, PAD, PH, REAR, RM, SIDE, SITE, SUITE, TH, UNIT, and UPPR. The geocoder will try to match variations of these values on input (e.g., UPR) and output the standardized value (e.g., UPPR).
unitNumber	String	The number of the unit, suite, or apartment within a house or building.
unitNumberSuffix	String	A letter that follows the unit number as in Unit 1A or Suite 302B.
civicNumber	String	The official number assigned to a site on a street by an address authority.
civicNumberSuffix	String	A letter or fraction that follows the civic number. There should be no space between a civic number and a letter (e.g., Unit 1A) and one space between a civic number and a fraction (e.g., Suite 3 ½)
streetName	String	The official name of the street recognized by a municipality (e.g., Douglas in 1175 Douglas Street). A streetName that starts with a directional is not abbreviated (e.g., North Park, not N Park).
streetType	String	The type of street as assigned by a municipality (e.g., the ST in 1175 DOUGLAS ST) and is abbreviated if such an abbreviation exists. The set of all street types is defined by the provincial Integrated Transportation Network program.
isStreetTypePrefix	Boolean	True if streetType should appear before streetName in fullAddress; false if streetType should appear after streetName
streetDirection	String	The abbreviated compass direction as defined by Canada Post and B.C. civic addressing authorities . The complete list is C, E, N, NE, NW, S, SE, SW, and W. All street directions except C are defined by Canada Post.
isStreetDirectionPrefix	Boolean	True if streetDirection should appear before street name in fullAddress; false if streetDirection should appear after streetName
streetQualifier	String	The qualifier of a street name (e.g., the Bridge in Johnson St Bridge)
localityName	String	The name of the municipality, community, Indian reservation, subdivision, regional district, aboriginal lands, or natural feature the site is located in. Since this standard is about geocoding, not mail delivery, the locality of a civic address is that defined by the civic address authority, not Canada Post. A locality name that starts with a directional is not abbreviated (e.g., North Vancouver, not N Vancouver). Spelling of localities that are place names or natural feature names MUST match that published by the BC Geographical Names Information System.
provinceCode	String	The ISO 3166-2 Sub-Country Code for British Columbia, which is BC.
X	Number	X coordinate of location (longitude in geographic projection, easting in other projections)
Y	Number	Y coordinate of location (latitude in geographic projection, northing in other projections)
srsCode	Integer	EPSG code of the spatial reference system that x,y are stated in. 
locationPositionalAccuracy	String	The accuracy of the coordinates representing the location of the site.
•	high if the point position was observed or measured using GPS or survey instruments, or digitized off imagery with a resolution of 1m or better.
•	medium if the point position was derived from parcel boundaries or from a point known to be inside a parcel. 
•	low if the point position was interpolated along a block face address range.
•	coarse if the point position represents an entire street, locality, or province.
locationDescriptor	String	Describes the nature of the location. Values include accessPoint, frontDoorPoint, localityPoint, parcelPoint, provincePoint, rooftopPoint, routingPoint, streetPoint
siteID	String	A unique identifier assigned to every site in B.C. They are currently not immutable. Poor matches and interpolated results don’t return a siteID.
blockID	String	ID of DRA road segment that site appears on
intersectionID	String	A unique and immutable identifier assigned to the intersection.
fullSiteDescriptor	String	That portion of addressString that precedes the civic number (in the case of a civic address) or the locality (in the case of a non-civic address).
narrativeLocation	String	Written directions to access the site. The narrative should start at the closest known, named physical feature to the site (e.g. from Tlell, travel north on highway 16 to the big golden spruce tree on your left, hike west for about one kilometre).
accessNotes	String	Additional information that is helpful in determining the access location and any restrictions on mode of access (e.g., boat only, floatplane only).
siteStatus	String	The status of the site (active, or retired). A site is usually retired when it is destroyed or combined with another site.
siteRetireDate	Date	The date the site was retired (in yyyy-mm-dd format)
changeDate	Date	The date a site was last changed ( in yyyy-mm-dd format)
isPrimary	Boolean	true if the location is the primary (or official) access point of the associated site; false otherwise.
degree	String	Degree of intersection (e.g., 3 for 3-way, 4 for 4-way etc.) 
