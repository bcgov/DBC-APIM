#Geocoder Glossary of Terms

Term | Definition
----: | -----------
<a name="accessNotes">accessNotes</a> | Contains additional information that is helpful in determining the access location and any restrictions on mode of access (e.g., boat only, floatplane only).
<a name="accessPoint">accessPoint</a> | The point on the curb or road edge and in the middle of the site’s driveway, access lane, or front entrance (if the site has no vehicle access).
<a name="accessPointRetireDate">accessPointRetireDate</a> | The date the access point was retired.
<a name="accessPointStatus">accessPointStatus</a> | The status of the access point (active, or retired). A civic access point is usually only Retired if the associated site is renumbered, destroyed, or combined with another site. A non-civic access point is usually retired when its associated site is assigned a civic number or the site becomes unoccupied.
<a name="Adaptive address interpolation">Adaptive Address Interpolation</a> | The process of inferring the location of a site with a given civic number using a road centreline, an address range, and other known site locations for a given block face.
<a name="addressString">addressString</a> | Civic address or intersection address as a single string in Single-line Address Format or a recognized alternative format.
<a name="Address match">Address match</a> | Conveys site address match quality through score, precision, and faults properties. faults is a data type that defines a list of faults. Each fault contains the nature of the fault, the address property affected, and the fault penalty. precisionPoints defines the points assigned to each match precision level. MatchPrecision is an enumeration of all precision levels. MatchFaultPenalty defines the penalty value of each possible fault. Penalties are subtracted from the appropriate precision level points to arrive at a match score.
<a name="blockID">blockID</a> | The unique, immutable identifier of a road segment in the Integrated Transportation Network that a matched address is located on.
<a name="bbox">bbox</a> | A rectangular geographic area used to filter results of a query. Coordinates are specified as xmin,ymin,xmax,ymax . By default, coordinates are longitude minimum, latitude minimum, longitude maximum, latitude maximum in the default output SRS, 4326 (WGS84).
<a name="changeDate">changeDate</a> | The date a site or intersection address was last changed.
<a name="Civic address">Civic Address</a> | The address of a site as assigned by an addressing authority such as a municipality. A civic address includes a civicNumber, civicNumberPrefix, and the localityName is that assigned by the address authority, not Canada Post.
<a name="civicNumber">civicNumber</a> | The number assigned to a site on a street by an address authority (e.g., the 1175 in 1175 Douglas St, Victoria, BC).
<a name="civicNumberSuffix">civicNumberSuffix</a> | 
<a name="aName">aName</a> | 
<a name="aName">aName</a> | 
<a name="aName">aName</a> | 
<a name="aName">aName</a> | 
<a name="aName">aName</a> | 
<a name="aName">aName</a> | 


<a name="aName">aName</a> | 

Civic Number Suffix (civicNumberSuffix)

Usually takes the form of a letter (e.g., as in 103A) or a fraction (as in 103 1/2).
Echo Unmatched Details (echo)

Include unmatched address details such as site name in results. Default is true.
End Date (endDate)

The ending date of a time period formatted as YYYY-MM-DD
Faults (faults)

Contains a list of faults the geocoder found with a given address match. Each fault contains the nature of the fault, the address property affected, and the fault penalty.
Faults include civicNumber.notInAnyBlock, civicNumberSuffix.notMatched, locality.notMatched, locality.isAlias, locality.spelledWrong, locality.missing, provinceCode.missing, provinceCode.notMatched, siteName.notMatched, streetName.notMatched, streetName.spelledWrong, streetType.missing, streetType.notMatched, streetDirection.missing, streetDirection.notMatched, unitDesignator.notMatched, unitNumber.notMatched, unitNumberSuffix.notMatched
Front Door Point (frontDoorPoint)

A point representing the position of the front door or main entrance to a house or building.
Full Address (fullAddress)

The full address of a site in a single string including unit number, site name, etc. as in:

    Johnson St and Douglas St, Victoria, BC
    Floor 1, 525 Superior St, Victoria, BC
    RM 104, Student Union Building | University of Victoria | 3800 Finnerty Rd, Saanich, BC

Note that site names have a site name suffix character ("|") for easier comprehension

Full Site Descriptor (fullSiteDescriptor)

The portion of fullAddress that precedes the civic number (in the case of a civic address) or the locality (in the case of a non-civic address).
Geomark (geomark)

A point, line, or polygon of interest that can be shared in a variety of formats and map projections. Geomarks are created by the Geomark Service.
Geomark URL (geomarkURL)

The URL of a polygon geomark that should be used by the geocoder as a bounding box in the /bgeo/sites/within query. Point and line geomarks will not work. When specifying this URL programmatically, it should be url-encoded without format and projection parameters.
Interpolated Site (interpolatedSite)

A site whose civic number is assumed to be valid because it lies within a known address range and whose location was interpolated using the address range (e.g., linear address interpolation) or the address range plus the locations of known sites (e.g., adaptive address interpolation).
Interpolation method (interpolation)

Interpolation method to use to determine location of matching site (adaptive, linear, none). Default is adaptive.
Intersection (intersection)

The intersection of two or more roads.
Intersection ID (intersectionID)

A unique and immutable identifier assigned to a given intersection in B.C.
Intersection Address (intersectionAddress)

The intersection of two or more named streets as a single string. Here are some examples:

    Douglas St and Gorge Rd E and Hillside Ave, Victoria, BC
    48th Ave W and Marine Dr SW, Vancouver, BC

Intersection Name (intersectionName)

The street name, type, and direction of all streets that meet at a given intersection. Here are some examples:

    Douglas St and Gorge Rd E and Hillside Ave
    48th Ave W and Marine Dr SW

Is Primary (isPrimary)

Is true if this is the primary (or official) access point of the associated site; false otherwise.
Items Per Page (itemsPerPage)

The number of results returned per page by the geocoder or other query. The default is 10. The last page returned may have fewer than this number.
Linear Address Interpolation (linearAddressInterpolation)

The process of inferring the location of a site with a given civic number using a road centreline and address range for a given block face.
Locality Is Alias (locality.isAlias)

A given civic number and street were found in an alias of the given locality but not the locality itself.
Locality Missing (locality.missing)

A given address didn’t contain a locality name but one was found that contains the given civic number and street.
Locality Name (localityName)

The name of the municipality, community, Indian reservation, subdivision, regional district, aboriginal lands, or natural feature the site is located in. Since this standard is about geocoding, not mail delivery, the locality of a civic address is that defined by the civic address authority, not Canada Post. A locality name that starts with a directional is not abbreviated (e.g., North Vancouver, not N Vancouver). Spelling of localities that are place names or natural feature names MUST match that published by the BC Geographical Names Information System.
Locality Not Matched (locality.notMatched)

A given locality does not contain a given civic number and street but another locality was found that does. 
Locality Spelled Wrong (locality.spelledWrong)

A given locality was spelled wrong but was successfully corrected to match a known locality.
Locality Type (localityType)

Can be a municipality, community, Indian reservation, subdivision, regional district, aboriginal lands, forward sortation area, or natural feature.
Location (location)

The coordinate pair of the matched location in the requested projection.
Location Accuracy (locationPositionalAccuracy)

    high – observed or measured using GPS or survey instruments, or digitized off imagery with a resolution of 1m or better
    medium – derived from parcel boundaries or from a point known to be inside a parcel
    low – interpolated along a block face address range
    coarse – position represents an entire street, locality, or province

Location descriptor (locationDescriptor)

Describes the nature of the address location. Values include accessPoint, frontDoorPoint, parcelPoint, rooftopPoint, and routingPoint.
Main Location (mainLocation)

A geometric point representing the rooftop, front door, or centre of the property.
Match Fault Penalty (matchFaultPenalty)

Defines the penalty value of each possible fault. Penalties are subtracted from the appropriate precision level points to arrive at a match score.
Match Precision (matchPrecision)

The level of precision of an address match. Here are the seven levels from the most precise to least precise:

    site – the site name matched
    unit – the unit number, unit number suffix, and unit designator matched
    civicNumber – the civic number matched
    intersection – the intersection matched
    block – the civic number falls within a known block range
    street – the street name, street direction, and street type matched
    locality – the locality matched
    Province - no match

Max distance (maxDistance)

The radius (in meters) used to define a bounding box in the bgeo/sites/nearest and bgeo/intersections/nearest queries.
Maximum Search Results (maxResults)

Maximum number of matched addresses to return for each input address. Default is 1.
Minimum Score (minScore)

Min score a match must have before it is included in the results. Default is 0. Scores range between 0 and 100 inclusive.
Narrative Location (narrativeLocation)

Contains written directions to access the site. The narrative should start at the closest known, named physical feature to the site (e.g. from Tlell, travel north on highway 16 to the big golden spruce tree on your left, hike west for about one kilometre).
Output Format (outputFormat)

Output file format (xhtml, kml, csv, shpz, geojson, geojsonp, gml)
Output SRS (outputSRS)

The EPSG code of the spatial reference system used to state the coordination location of a named feature. It is ignored if KML output is specified since KML only supports 4326 (WGS84). Allowed values are:

    3005: BC Albers
    4326: WGS 84 (default)
    26907-26911: NAD83/UTM Zones 7N through 11N
    32607-32611: WGS84/UTM Zones 7N through 11N
    26707-26711: NAD27/UTM Zones 7N through 11N

Parcel Point (parcelPoint)

A point representing a position known to be within the boundaries of a land parcel, usually the parcel centroid.
Point (pointCoordinates)

The coordinates of the centre point used to define a bounding box in the bgeo/sites/nearest and bgeo/intersections/nearest queries . Format is x,y where x and y are coordinates in the specified outputSRS projection. By default, x is longitude and y is latitude in the default outputSRS projection of 4326 (WGS84).
Precision Points (precisionPoints)

Defines the points assigned to each match precision level.
Province Code (provinceCode)

The ISO 3166-2 Sub-Country Code for British Columbia, which is BC.
Province Code Missing (provinceCode.missing)

A given input address (addressString) representing a civic address or intersection address included a Province (provinceCode) that did not match with 'BC'. A match with the correct provinceCode is returned.
Province Code Not Matched (provinceCode.notMatched)

A given input address (addressString) representing a civic address or intersection address included a Province (provinceCode) that did not match with 'BC'. A match with the correct provinceCode is returned.
Rooftop Point (rooftopPoint)

A point representing the roof of a house or building.
Routing Point (routingPoint)

A point lying on a road centreline and directly in front of a site's accessPoint. A routing point is intended for use by routing algorithms to finding routes between addresses.
Score (score)

A number between 0 and 100 representing the quality of an address match; 100 is a perfect match; 0 means no match. Score is computed by taking the precision points and subtracting penalty points for each fault found.
Setback (setBack)

The distance to set back the returned point location from the curb(in meters). A positive setback moves the location toward the interior of the parcel, a setback of zero returns the location of the curb, and a negative setback returns the location of the street centreline. Setback is only used for interpolated site results.
Site (site)

A constructed geographic feature in British Columbia with known coordinates (latitude/longitude) and a site address that is needed in the conduct of provincial business. Examples of constructed geographic features include houses, cabins, permanent campsites, mobile home and RV parks, units within houses and buildings, buildings within complexes, stores, malls, offices, industrial plants, bandshell, golf courses, hospitals, universities, recreation centres, places of worship, parks, municipal pumping stations, hydro sub-stations, wharves, airports, train stations, and landmarks.
Site ID (siteID)

A unique identifier assigned to every site in B.C. They are currently not immutable. Poor matches and interpolated results don’t return a siteID.
Site Name (siteName)

A string containing the name of the building, facility, or institution (e.g., Duck Building, Casa Del Mar, Crystal Garden, Bluebird House). A business name should only be used if it is permanently affixed to the site and the site has no other, more generic name. If a site is a unit within a complex, it may have a sitename in addition to a unitNumber and unitSuffix. siteName may be empty.
Site Name Not Matched (siteName.notMatched)

A matching address was found but it does not have a site name or match the one provided.
Site Retire Date (siteRetireDate)

The date the site was retired.
Site Status (siteStatus)

The status of the site (active, or retired). A site is usually retired when it is destroyed or combined with another site.
SRS Code (spatialReferenceSystem)

The code of the spatial referencing system that Location is defined in. Supported codes are:

    4326 - lat/lon
    3005 - BC Albers
    26907-26911 - NAD83 UTM zones 7 - 11

Start Date (startDate)

The starting date of a time period formatted as YYYY-MM-DD
Start Index (startIndex)

The index number of the first result that the geocoder or other query should return. The first result is assigned an index of 1 which is also the default.
Street Centreline (streetCentreline)

A line that is parallel to the street edges and located in the middle of the roadway. A street centreline exists even on streets that have no painted lines on them (e.g., a residential or unpaved street). A street centreline is oriented in the direction of increasing civic numbers. In the case of blocks that have continuous numbering that goes up on one side and down the other the street centreline is oriented in the direction of the lowest block range.
Street Direction (streetDirection)

The abbreviated compass direction as defined by Canada Post and B.C. civic addressing authorities . The complete list is C, E, N, NE, NW, SE, SW, and W. All street directions except C are defined by Canada Post.
Street Direction Missing (streetDirection.missing)

A given address didn’t contain a street direction for a given street name and street type in a given locality but one was found.
Street Direction Not Matched (streetDirection.notMatched)

A given street direction for a given street name and street type in a given locality was not found. A match without the street direction is returned.
Street Name (streetName)

The official name of the street recognized by a municipality (e.g., Douglas in 1175 Douglas Street). A streetName that starts with a directional is not abbreviated (e.g., North Park, not N Park)
Street Name Not Matched (streetName.notMatched)

A given street name within a given locality was not found. The locality is returned with a match precision of LOCALITY. Other addresses in different localities that contain the given civic number and street will also be returned but with a lesser score.
Street Name Spelled Wrong (streetName.spelledWrong)

A given street name was spelled wrong but was successfully corrected to match a known street name with the given locality.
Street Type (streetType)

The type of street as assigned by a municipality (e.g., the ST in 1175 DOUGLAS ST) and is abbreviated if such an abbreviation exists. The set of all street types is defined by the provincial Digital Road Atlas program.
Street Type Missing (streetType.missing)

A given address didn’t contain a street type for a given street name in a given locality but one was found.
Street Type Not Matched (streetType.notMatched)

A given street type for a given street name in a given locality was not found. A match containing the correct street type is returned.
Unit Number (unitNumber)

The number of the unit, suite, or apartment within a house or building.
Unit Number Not Matched (unitNumber.notMatched)

A matching address was found but it does not have a unit number or match the one provided.
Unit Number Suffix (unitNumberSuffix)

A letter or fraction that follows the unit number as in Unit 1A or Suite 1 1/2.
Unit Number Suffix Not Matched (unitNumberSuffix.notMatched)

A matching address was found but it does not have a unit number suffix or match the one provided.
Unit Designator (unitDesignator)

The type of unit(e.g., APT, SUITE, and UNIT) and is abbreviated if such an abbreviation is defined. The set of all unit designators MUST include those defined in the Addressing Guidelines by Canada Post and is the responsibility of DataBC.
Unit Designator Not Matched (unitDesignator.notMatched)

A matching address was found but it does not have a unitDesignator or match the one provided.
