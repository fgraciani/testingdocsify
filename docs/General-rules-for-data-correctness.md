`GENERAL GUIDANCE`

*Important note: in the present version of the document, limited effort
could be spent on the documentation of FIXM business rules addressing
data correctness. The list below provides an initial set of rules that
were identified during the writing of this document or that are already
captured in the FIXM model as model element notes. Future versions of
the document will enrich this table based on implementers’ feedback, and
may also revisit the overall formulation and description method for
these rules, in particular in the light of the [AIXM experience with
regards to business rules](http://aixm.aero/page/business-rules).*

|FIXM model element|Business rule description|
|:-|:-----|
|GeograhicalPosition|When encoding geographical positions, special values INF, -INF and NaN are not allowed.|
|ContactInformation,<p>PersonOrOrganization|If the usage of ContactInformation is associated with a person, the ContactInformation.name field should not be used and the PersonOrOrganization.name should be used instead.|
|PostalAddress|The countryName shall always be populated with the full name, not an ISO 3166 abbreviation.|
|PostalAddress|CountryCode shall always be populated using an ISO 3166 abbreviation.|
|OnlineContact|If OnlineContact.network.type=INTERNET, the OnlineContact.linkage shall be expressed as a valid URL.|
|OnlineContact|If OnlineContact.network.type=AFTN, the OnlineContact.linkage shall be expressed as a valid AFTN address.|
|AerodromeReference|The locationIndicator shall be a valid code provided by ICAO Doc 7910.|
|VerticalRange|The lowerBound shall always be lower than the upperBound.|
|TrueAirspeedRange|The lowerSpeed shall always be lower than the upperSpeed.|
|TimeRange|The earliest time shall always be before the latest time.|
|Aircraft|The property formationCount, if provided, shall be equal to or greater than 2.|
|Aircraft, AircraftType|The sum of all the AircraftType.numberOfAircraft properties, if provided, shall match Aircraft.formationCount.|
|OnlineContact|The OnlineContact.network shall be always populated when providing an OnlineContact.linkage.|
