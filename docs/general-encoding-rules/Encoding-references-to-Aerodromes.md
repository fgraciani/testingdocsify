`GENERAL GUIDANCE`

`FIXM TYPE` [fb:AerodromeReferenceType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_AerodromeReferenceType.html#LinkC)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/AerodromeReferenceType.png">

***

**OPTION 1 - Minimum reference**

The minimum aerodrome reference shall consist of the aerodrome location
indicator, if provided by ICAO Doc 7910 \[11\]. If the aerodrome has no
ICAO Doc 7910 location indicator, the minimum aerodrome reference shall
consist of the name of the aerodrome and its geographical location,
namely the aerodrome reference point.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

CASE 1 – The Aerodrome has an ICAO Doc 7910 location indicator

```xml
<fx:destinationAerodrome>
   <fb:locationIndicator>EADD</fb:locationIndicator>
</fx:destinationAerodrome>
```

CASE 2 – The Aerodrome has no ICAO Doc. 7910 location indicator

```xml
<fx:destinationAerodrome>
   <fb:name>DONLON</fb:name>
   <fb:referencePoint srsName="urn:ogc:def:crs:EPSG::4326">
      <fb:pos>52.3716666666667 -31.9494444444444</fb:pos>
   </fb:referencePoint>
</fx:destinationAerodrome>
```

***

**OPTION 2 - Minimum reference with supplementary AIXM pointer**

*(OPTION 2 = OPTION 1 + supplementary hypertext reference)*

Option 2 corresponds to Option 1 with an additional hypertext reference
as described in chapter Generic hypertext references.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

CASE 1 – The Aerodrome has an ICAO Doc 7910 location indicator

```xml
<fx:destinationAerodrome href="urn:uuid:1b54b2d6-a5ff-4e57-94c2-f4047a381c64">
   <fb:locationIndicator>EADD</fb:locationIndicator>
</fx:destinationAerodrome>
```

CASE 2 – The Aerodrome has no ICAO Doc. 7910 location indicator

```xml
<fx:destinationAerodrome href="urn:uuid:1b54b2d6-a5ff-4e57-94c2-f4047a381c64">
   <fb:name>DONLON</fb:name>
   <fb:referencePoint srsName="urn:ogc:def:crs:EPSG::4326">
      <fb:pos>52.3716666666667 -31.9494444444444</fb:pos>
   </fb:referencePoint>
</fx:destinationAerodrome>
```

***

**Important note**

FIXM enables the encoding of richer aerodrome
“reference” structures, such as

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:destinationAerodrome href="urn:uuid:1b54b2d6-a5ff-4e57-94c2-f4047a381c64">
   <fb:iataDesignator>DLN</fb:iataDesignator>
   <fb:locationIndicator>EADD</fb:locationIndicator>
   <fb:name>DONLON</fb:name>
   <fb:referencePoint srsName="urn:ogc:def:crs:EPSG::4326">
      <fb:pos>52.3716666666667 -31.9494444444444</fb:pos>
   </fb:referencePoint>
</fx:destinationAerodrome>
```

The provision of the name and reference point in addition to the
location indicator is technically possible but does not serve the
purpose of identifying the aerodrome. This implementation practice only
aims to provide consumers with richer information about the aerodrome
being referred to. Whether or not to use this supplementary information
is at the discretion of the consuming system / service.
