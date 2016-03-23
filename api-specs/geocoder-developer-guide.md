#BC Physical Address Geocoder
##Developer Guide
This guide is aimed at developers and web masters that would like to incorporate the Physical Address Geocoder into their applications and websites.
<br>
###Introduction
The BC Physical Address Online Geocoder REST API lets you integrate real-time standardization, validation, and geocoding of physical addresses into your own applications. This document defines the REST API. 
To simplify integration of the online geocoder into your client web application, you can use the Javascript API located at:
http://apps.gov.bc.ca/pub/geocoder/js/geocode.js 
<br>
###API Changes in v2.0
1.	A site can now have one or more public or related business occupants. Here is an example:
VICTORIA LAW COURTS -- 850 Burdett Ave, Victoria, BC
Resources have been added to support validating, geocoding, and finding occupants nearby but only courts of law and some hospitals have been loaded. Expect a lot more occupants in the near future. Here are some example requests:
http://apps.gov.bc.ca/pub/geocoder/occupants/addresses.geojson?tags=courts&addressString=victoria%20law%20courts%20--%20
http://apps.gov.bc.ca/pub/geocoder/occupants/nearest.geojson?point=-123.7064038,48.8498537&tags=courts 
http://apps.gov.bc.ca/pub/geocoder/occupants/near.geojson?point=-123.7064038,48.8498537&tags=courts&maxResults=3
2.	The documentation has been updated.

###Resource Overview
The Online Geocoder offers resources for validating and geocoding an address (including public and related business occupants); finding a given site, intersection, and occupant; and finding sites, intersections, and occupants near a point or within an area.
Geocoder Base URL
The current baseUrl for the online geocoder is:
http://apps.gov.bc.ca/pub/geocoder
The baseUrl for the online geocoder under the HTTP Secure protocol is: 
https://apps.gov.bc.ca/pub/geocoder
###Addresses Resource
The addresses resource represents all addresses in the geocoder. A request on this resource to find a query address will return one or more matching addresses that are standardized and geocoded (i.e., given a point location on the earth). 
A query address can be specified in two different ways:
1.	A single address string containing all elements of an address as in:
http://apps.gov.bc.ca/pub/geocoder/addresses.geojson?addressString=525%20superior%20st,%20victoria,%20bc 
2.	A set of address elements as in:
http://apps.gov.bc.ca/pub/geocoder/addresses.geojson?civicNumber=525&streetName=superior&streetType=st&localityName=victoria&provinceCode=BC 
This request will execute faster and may return a better match for the same address since the geocoder doesn’t have to determine what each part of an address string means.

Here are some more example geocoder requests:

1.	Geocode 456 Gorge Rd E, Victoria, BC<br> 
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?addressString=456%20Gorge%20Rd%20e%20victoria%20bc<br><br>
2.	Geocode 7-955 13th Ave, Valemount, BC<br>
http://apps.gov.bc.ca/pub/geocoder/addresses.xhtml?addressString=7-955%2013th%20ave,%20Valemount,bc<br><br> 
3.	Geocode the intersection at Johnson and Government<br><br>
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
