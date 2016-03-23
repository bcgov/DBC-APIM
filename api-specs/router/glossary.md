#BC Route Planner Glossary of Terms
Term | Definition
----: | -----------
<a name="criteria">criteria</a> | Routing criteria to optimize. One of shortest or fastest. Default is shortest.
<a name="distanceUnit">points</a> | Unit of measure to report distance value in. One of km (kilometres) or mi (miles). Default is km.
<a name="outputFormat">outputFormat</a> | Format of representation. One of json, html, and kml. Default is json.
<a name="points">points</a> | A list of any number of route points in start to end order. Points are specified as X1,Y1,...Xn,Yn where X and Y are values in the projection specified by the 'outputSRS' parameter. If no outputSRS is given, X is treated as longitude and Y is treated as latitude.<br>Here is an example:<br>-123.707942,48.778691,-123.537850,48.382005<br><br>To make a round trip, just add the start point as in:<br>-123.707942,48.778691,-123.537850,48.382005,-123.707942,48.778691
<a name="routeDescription">routeDescription</a> | A short description of the nature of the requested route. This will be echoed in the returned route representation for use in your application. For example:<br>Fastest route from 1002 Johnson St, Victoria to 1105 Royal Ave, New Westminster" 

