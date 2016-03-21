#Geocoder Faults
Name | Definition
-------: | ---------------
<a name="civicNumberMissing">Civic Number Missing</a> | A given address didn't contain a civic number but one was found.
Civic Number Not In Any Block | A given civic number is not in any known address range for a given street in a given locality. The street within the given locality is returned with a match precision of STREET. 
Civic Number Suffix Not Matched | A given civic number suffix for a given civic number and street was not found in a given locality.
Locality Is Alias	| A given civic number and street were found in an alias of the given locality but not the locality itself.
Locality Missing | A given address didn’t contain a locality name but one was found that contains the given civic number and street.
Locality Not Matched | A given locality does not contain a given civic number and street but another locality was found that does.
Locality Spelled Wrong | A given locality was spelled wrong but was successfully corrected to match a known locality. 
Postal Address Element Not Allowed | An element of a mailing address was detected (e.g., PO, BOX nn, SS, RR nn, a postal code. All such elements are ignored.
Province Missing | A given address didn't contain a province code (e.g., BC)
Province Not Matched |	A province code other than BC was found 
Site Name missing |	A given address didn't contain a site name but one was found.
Site Name Not Matched | A given site name was not found. A match without a site name is returned.
Site Name Partially Matched | Some of the words in a site name were matched. A match with a full site name is returned.
Site Name Spelled Wrong |	A given site name was spelled wrong but was successfully matched to a known site.
Street Missing | A given address didn't contain a street but one was found.
Street Direction Missing | A given address didn’t contain a street direction for a given street name and street type in a given locality but one was found.
Street Direction Not Matched | A given street direction for a given street name and street type in a given locality was not found. A match without the street direction is returned.
Street Direction Spelled Wrong | A given street direction was spelled wrong. A match with a correctly spelled street direction is returned.
Street Name Is Alias | A given street name is an alias for the official street name. A match with the official street name is returned.
Street Name Missing | A given address didn't contain a street name but one was found.
Street Name Not Matched | A given streetName within a given locality was not found. The locality is returned with a match precision of LOCALITY. Other addresses in different localities that contain the given civic number and street will also be returned but with a lesser score.
Street Name Spelled Wrong | A given street name was spelled wrong but was successfully corrected to match a known street name with the given locality.
Street Qualifier Missing | A given address didn't contain a street qualifier but one was found.
Street Qualifier Not Matched | A given street qualifier was not found. A match without a street qualifier is returned.
Street Qualifier Spelled Wrong | A given street qualifier was spelled wrong but was successfully corrected to match a known street qualifier.
Street Type Missing | A given address didn’t contain a street type for a given street name in a given locality but one was found.
Street Type Not Matched | A given street type for a given street name in a given locality was not found. A match containing the correct street type is returned.
Street Type Spelled Wrong |	A given street type was spelled wrong but was successfully corrected to match a known street type.
Unrecognized element notAllowed	| A potential street name or locality name isn’t known anywhere in the province (e.g., Gazoony St).  Since geocoder v1.4, the parser gives up, keeping execution time short. In v1.3, the parser would not give up until it returned a more meaningful fault like streetName notMatched but this took too long.
Unit Designator Is Alias | A given unit designator is an alias of the official unit designator. A match containing the official unit designator is returned.
Unit Designator Missing | A given address didn't contain a unit designator but one was found.
Unit Designator Not Matched | A given unit designator was not found. A match containing the correct unit designator is returned.
Unit Designator Spelled Wrong | A given unit designator was spelled wrong but was successfully corrected to match a known unit designator.
Unit Number Missing | A given address didn't contain a unit number but one was found.
Unit Number Not Matched | A given unit number was not found. A match containing the correct unit number is returned.
Unit Number Suffix missing | A given address didn't contain a unit number suffix but one was found.
Unit Number Suffix Not Matched | A given unit number suffix was not found. A match containing the correct unit number suffix is returned.
