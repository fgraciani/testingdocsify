`GENERAL GUIDANCE`

# What is FIXM Core?

**FIXM Core** provides globally harmonized flight data structures that
can be exchanged in various contexts. The main context for the use of
**FIXM Core** is ICAO FF-ICE. Therefore, **FIXM Core** currently
captures the flight data structures that are identified in the ICAO
FF-ICE Implementation Guidance Manual 0.91. Only flight data structures
that are globally applicable qualify for FIXM Core. Flight data
structures that are local or regional in nature do not qualify for
**FIXM Core**. An **Extensions** mechanism is implemented so that **FIXM
Core** can be extended in order to cover these local or regional data
structures, as appropriate.

**FIXM Core** exists as a standard for exchanging flight data rather
than as a set of pre-defined messages, allowing flexible exchanges
between users rather than enforcing rigid communication patterns.
However, once a given exchange is well-defined, it is useful to be able
to enforce syntax and content validation checks to ensure the data being
exchanged is of high quality. This is addressed by **Application
Libraries**.

# What is a valid FIXM Core usage?

The general requirements for a valid **FIXM Core** usage are the
following:

## Requirement on data structure

| **To qualify as valid usage of FIXM Core, the flight-related content of a given message, or relevant part thereof, shall be syntactically valid against the FIXM Core XML Schemas.**|
|:---|

`RATIONALE` The valid usage of FIXM Core implies that the flight-related content of a message exchanged between two parties is valid against the FIXM Core XML Schemas. If a message includes additional information not in scope of FIXM Core, it must be structured so that its relevant part is valid against the FIXM Core XML Schemas.

`IMPORTANT NOTE` Being syntactically valid against the FIXM Core XML Schemas implies the FIXM Core hierarchy is respected. FIXM Core is not expected to be used only as a library of flight datatypes.

`HOW TO CHECK THIS` The content of a message, or relevant part thereof, validates without error against the FIXM Core XML schemas when tested / parsed by XML validation tools.


`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:aerodrome>
   <fb:locationIndicator>EBBR</fb:locationIndicator>
</fx:aerodrome>
```

This example displays an aerodrome reference involving a four-letter
ICAO location indicator. It complies with the structural rules for
aerodrome references defined by the FIXM Core XML schemas.


`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/nok.png" width="20" height="20" />

```xml
<fx:aerodrome>
   <fb:locationIndicator>BRU</fb:locationIndicator>
</fx:aerodrome>
```

This example displays an aerodrome reference based on property
locationIndicator. The value “BRU” does not respect the pattern
\[A-Z\]{4} enforced by FIXM for property locationIndicator. This example
does NOT comply with the structural rules for aerodrome references
defined by the FIXM XML schemas and does not qualify as valid FIXM
usage.


`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/nok.png" width="20" height="20" />

The example below features a valid XML schema that defines a Flight
Identification structure comprising the departure & arrival aerodrome
references, the aircraft identification and the estimated off-block
time. It also features an example XML sample that is valid against this
schema.

```xml
<xs:schema xmlns:wrong="fixm_as_library_of_types" xmlns:fx="http://www.fixm.aero/flight/4.2" xmlns:fb="http://www.fixm.aero/base/4.2" […] >  
[…]
   <xs:element name="FlightIdentification" type="wrong:FlightIdentificationType"/> 
   <xs:complexType name="FlightIdentificationType"> 
      <xs:sequence> 
         <xs:element name="departureAerodrome" type="fb:AerodromeReferenceType"/> 
         <xs:element name="arrivalAerodrome" type="fb:AerodromeReferenceType"/> 
         <xs:element name="ACID" type="fb:AircraftIdentificationType"/> 
         <xs:element name="EOBT" type="fb:TimeType"/> 
      </xs:sequence> 
   </xs:complexType> 
</xs:schema>
```
<img src="./media/Double_arrow_symbol_-_blue.png" style="width:0.50in;height:0.70in" />

```xml
<wrong:FlightIdentification xmlns:wrong=[…] xmlns:fb="http://www.fixm.aero/base/4.2" xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:schemaLocation=[…]>
   <wrong:departureAerodrome>
      <fb:name>LES BARAQUES</fb:name>
   </wrong:departureAerodrome>
   <wrong:arrivalAerodrome>
      <fb:name>NORTHFALL MEADOW</fb:name>
   </wrong:arrivalAerodrome>
   <wrong:ACID>BLXI</wrong:ACID>
   <wrong:EOBT>1909-07-25T04:41:00.000Z</wrong:EOBT>
</wrong:FlightIdentification>
<!-- https://en.wikipedia.org/wiki/Louis\_Bl%C3%A9riot\#1909\_Channel\_crossing -->
```


The example schema above is not FIXM Core and is not a FIXM extension.
It is a fictitious, standalone XML schema that defines its own hierarchy
of elements, but which reuses types from the core FIXM XML schemas for
typing these elements. The reuse of FIXM datatypes is highlighted in
blue in the schema description.

This example illustrates the reuse of FIXM Core as a library of
datatypes. While this practice is technically feasible and produces
valid schemas, it is not considered a valid FIXM Core usage because it
breaks the hierarchy of properties defined by FIXM Core. An information
service relying on such an implementation practice would fail to satisfy
the FIXM Core requirement on data structure.

## Requirement on data correctness

| **To qualify as valid usage of FIXM core, the flight-related content of a given message, or relevant part thereof, shall satisfy the minimum set of rules addressing data plausibility and consistency.** |
|:---|

`RATIONALE` The flight-related content of a message being syntactically correct and complete may still not make sense from an operational or plausibility perspective. Additional business rules are required to check the correctness of the encoded information, such as the consistency between model elements.

`HOW TO CHECK THIS` The content of a message, or the relevant part thereof, validates without error against the applicable business rules addressing data correctness. Chapter 2.4.13 lists business rules addressing data correctness which are always applicable whatever the context of the exchange. Additional business rules addressing data correctness may exist which are specific to particular use-cases.


`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:verticalRange>
   <fb:lowerBound>
      <fb:flightLevel uom="FL">240</fb:flightLevel>
   </fb:lowerBound>
   <fb:upperBound>
      <fb:flightLevel uom="FL">250</fb:flightLevel>
   </fb:upperBound>
</fx:verticalRange>
```

This example shows the FIXM encoding of vertical range \[FL240;FL250\].
It satisfies the basic data plausibility/correctness rule “*The
lowerBound shall always be lower than the upperBound*” that is
identified in Chapter 2.4.13. It qualifies as valid FIXM core usage.



`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/nok.png" width="20" height="20" />

```xml
<fx:aircraft>
   <fx:aircraftType>
      <fx:numberOfAircraft>2</fx:numberOfAircraft>
	  <fx:type>
         <fx:icaoAircraftTypeDesignator>MIR2</fx:icaoAircraftTypeDesignator>
      </fx:type>
   </fx:aircraftType>
   <fx:aircraftType>
      <fx:numberOfAircraft>1</fx:numberOfAircraft>
      <fx:type>
         <fx:icaoAircraftTypeDesignator>RFAL</fx:icaoAircraftTypeDesignator>
      </fx:type>
   </fx:aircraftType>
   <fx:formationCount>2</fx:formationCount>
</fx:aircraft>
```

This example represents a description of a fictitious formation of
military aircraft composed of two Mirages 2000 and one Rafale which
altogether constitute a single (formation) flight. This example is valid
from a data structure point of view (it validates against the FIXM core
XML schemas) but is not correct in so far as the sum of all
AircraftType.numberOfAircraft properties does not match
Aircraft.formationCount, which breaks a rule from Chapter 2.4.13. This
example does not qualify as valid FIXM core usage.
