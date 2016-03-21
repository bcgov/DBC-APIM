#Single-Line Address Format

An address may be represented by a single line (string) in one of the formats listed below. 

In each format, a term in square brackets is optional, a term in square brackets followed by an asterisk means the term may appear zero or more times, and a term in square brackets followed by a plus sign means the term may appear one or more times.  A term in brace brackets (e.g., {streetDirection}) may appear in none or one of the multiple places indicated (e.g., Central St, N Central St, or Central St N, but not N Central St NE). frontGate is the double dash delimiter (e.g., “--“) 

##Format 1 – Civic address

{occupantName[,]}[[unitDesignator unitNumber[unitNumberSuffix]] [siteName],]* frontGate civicNumber[civicNumberSuffix] {streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier], localityName, provinceCode


##Format 2 – Non-civic address

{occupantName[,]}[[unitDesignator unitNumber[unitNumberSuffix]] [siteName],]* frontGate [{streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier],] localityName, provinceCode


##Format 3 – Intersection address

{streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier] [ and {streetDirection} {streetType} streetName {streetType} {streetDirection} [streetQualifier] ]+ , localityName, provinceCode


##Examples

###Example 1 - Civic Address

420A GORGE RD E, VICTORIA, BC

which contains the following address elements:

Address Element |	Value
----: | -----------
civicNumber |	420
civicNumberSuffix |	A
streetName |	GORGE
streetType |	RD
streetDirection |	E
localityName |	VICTORIA
provinceCode |	BC


###Example 2 - Civic address with unit

UNIT 1A -- 433 CEDAR RAPIDS BLVD, PEMBERTON, BC 

which contains the following address elements:

Address Element |	Value
----: | -----------
unitDesignator |	UNIT
unitNumber |	1
unitNumberSuffix |	A
civicNumber |	433
streetName |	CEDAR RAPIDS
streetType |	BLVD
localityName |	PEMBERTON
provinceCode |	BC

Example #3 - Non-civic address with a street qualifier:

JOHNSON ST BRIDGE, VICTORIA, BC 

which contains the following address elements:

Address Element |	Value
----: | -----------
streetName |	JOHNSON
streetType |	ST
streetQualifier |	BRIDGE
localityName |	VICTORIA
provinceCode |	BC

Example #4 - Civic addresses without a unit

1025 HAPPY VALLEY RD, METCHOSIN, BC 
130A HILL ST, NELSON, BC 

3.	Civic addresses with occupants: 

PORT ALICE HEALTH CENTRE -- 1090 MARINE DRIVE, PORT ALICE, BC 
ROYAL ATHLETIC PARK -- 1014 CALEDONIA AVE, VICTORIA, BC 

4.	Civic addresses with a unit within a named complex: 

PAD 2, HAPPY MOBILE HOME PARK -- 1200 NORTH PARK RD, SHAWNIGAN LAKE, BC 
ROOM 103A, CLEARIHUE BUILDING, UNIVERSITY OF VICTORIA -- 3800 FINNERTY RD, VICTORIA, BC 
ROOM 230, WEST BLOCK, ROYAL JUBILEE HOSPITAL -- 1952 BAY ST, VICTORIA, BC 

5.	Non-civic addresses with a unit within a named complex: 

PAD 2, HAPPY MOBILE HOME PARK -- NIMPO LAKE, BC 
PAD 2, HAPPY MOBILE HOME PARK -- REMOTE RD, NIMPO LAKE, BC 


6.	Non-civic address containing a street, locality, and  province: 

WILLOW DRIVE, 70 MILE HOUSE, BC 
HORSE LAKE ROAD, 100 MILE HOUSE, BC
JOHNSON ST BRIDGE, VICTORIA, BC 

7.	Non-civic addresses containing only  locality and province: 

PEACE RIVER REGIONAL DISTRICT, BC 
100 MILE HOUSE, BC 
PYPER LAKE, BC 

8.	Intersection addresses: 

Douglas St and Johnson St, Victoria, BC
Douglas St and Gorge Rd E and Hillside Ave, Victoria, BC

 
Alternative Address Formats
On input, the GET geocoder/addresses request can also handle the following alternatives to single-line address format:

1.	Unit without a frontGate:
PAD 2, 1200 NORTH PARK RD, SHAWNIGAN LAKE, BC 

2.	Unit number without a frontGate and unitDesignator (as per Canada Post):
2-1200 NORTH PARK RD, SHAWNIGAN LAKE, BC 

3.	Unit following street (as per Canada Post):
1200 NORTH PARK RD PAD 2, SHAWNIGAN LAKE, BC 

