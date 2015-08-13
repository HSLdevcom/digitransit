Many terms related to public transportation have multiple meanings for different speakers.
In addition translations between English and Finnish might be unintuitive,
as the most similar word in the other language might refer to different thing.

This page defines the vocabulary used in the project source code and documentation.

Terms also used in GTFS or OpenTripPlanner are marked.


<dl>
    <dt>route (GTFS, OTP), linja</dt>
    <dd>Public transport service shown to customers under a single name, usually from point A to B and back. For example: trams <strong>1</strong> and <strong>1A</strong>, buses <strong>18</strong> and <strong>102T</strong>, or train <strong>A</strong>.
        Commonly used synonyms: <i>line</i></dd>

    <dt>pattern (OTP)</dt>
    <dd>Sequence of stops as used by a specific direction and variant of a route. For example a tram entering/departing service from/to the depot usually joins at the middle of the route,
        or a route might have a short term diversion (<i>poikkeusreitti</i>) without changing the route name (longer diversions usually are marked as different routes).
        </dd>

    <dt>block (GTFS)</dt>
    <dd>If customers can stay aboard a vehicle that changes its route, the trips belong to the same <em>block</em>.
        For example tram 2 arriving to Olympialaituri departs as tram 3: 2 and 3 are opposite sides on a circular route.
        </dd>

    <dt>timepoint (GTFS), (ajan)tasauspysäkki</dt>
    <dd>A stop for a route where the vehicle will not depart until the scheduled departure time.
        </dd>

    <dt>trip (GTFS, OTP), lähtö / vuoro</dt>
    <dd>A specific occurance of a route, usually identified by the route and exact departure time from the first stop. For example bus 102 leaving from Otaniemi on 2015-05-01 10:00, or more generally (e.g. a GTFS trip) leaving from Otaniemi at 10:00 on specified days (e.g. Monday to Friday from 2015-08-10 to 2016-05-31 excluding holidays).
        </dd>

    <dt>service (GTFS)<dt>
    <dd>Combination of trips that operate on certain weekdays (given in GTFS calendar.txt), with exceptional missing and additional days (calendar_dates.txt) for a given time period (from date A to date B).</dd>

    <dt>(transportation) mode, kulkumuoto</dt>
    <dd>Means of transport, for example: walking, cycling, driving a car, bus, train, subway, tram, ferry, taxi, airplane.
        </dd>

    <dt>itinerary, reitti</dt>
    <dd>Combination of different transportation modes at certain times to reach from origin to destination.
        For example to go from Pasila (Helsinki) to Koskikeskus (Tampere) you could walk to the train station, take the 14:00 P train to Aviapolis, walk to the airport, take the 15:00 flight to Tampere-Pirkkala,
        take a taxi to destination.
        Commonly used synonyms: <i>journey</i></dd>

    <dt>leg</dt>
    <dd>One part of an itinerary.
        </dd>

    <dt>origin, lähtöpaikka</dt>
    <dd>When the context is a person; the geographical point where an itinerary begins.
        When the context is a route; the first stop on the route or the first location on the headsign.
        </dd>

    <dt>destination, määränpää</dt>
    <dd>When the context is a person; the geographical point where an itinerary ends.
        When the context is a route; the last stop on the route or the last location on the headsign.
        </dd>

    <dt>headsign, linjakilpi</dt>
    <dd>Description of a route usually written on the front of the vehicle.
        For example: "Helsinki" (for just the destination) or "Helsinki - Tampere" (for both the origin and destination).
        </dd>

    <dt>position, sijainti</dt>
    <dd>The current location of a user, usually measured with GPS.
        <strong>Note:</strong> <i>geolocationing</i> is used as the technical term for acquire the position with the instruments in the user's device.
        </dd>

    <dt>location, paikka</dt>
    <dd>A geographical point where something is, usually given as coordinates.
        </dd>

    <dt>point of interest / POI</dt>
    <dd>A public service or amenity (eg. a hospital or a church), a landmark (eg. the Sibelius monument), business (eg. ABC fuel station)
        or other geographical place of general interest.
        </dd>

    <dt>(reverse) geocoding</dt>
    <dd>Finding the location (coordinates) of something, for example an address or a POI.
        Reverse geocoding is determining the human readable textual form for coordinates, and is inherently ambiguous because places can have both addresses and names.
        </dd>

    <dt>Helsinki Regional Transport Authority HSL / Helsinki Region Transport HSL, HSL Helsingin seudun liikenne</dt>
    <dd>The public transportation agency in Helsinki region.
        </dd>

    <dt>JORE / joukkoliikennerekisteri</dt>
    <dd>"Public transportation registry". The database of HSL for public transportation in the Helsinki region.
        </dd>

    <dt>Vallu</dt>
    <dd>Public transportation registry of Finnish Transport Agency for all long distance public transportation in Finland.
        </dd>

    <dt>Kalkati</dt>
    <dd>An XML format used for Vallu exports.
        </dd>

</dl>
