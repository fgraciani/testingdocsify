`GENERAL GUIDANCE`

`FIXM TYPE` [fb:NavaidType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_NavaidType.html#Link16)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/NavaidType.png">

***

**OPTION 1 - Minimum reference**

As a minimum, the coded designator of a navaid shall be provided, as
published in the AIPs.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fb:navaid>
   <fb:designator>BOR</fb:designator>
</fb:navaid>
```

***

**OPTION 2 - Unambiguous reference**

*(OPTION 2 = OPTION 1 + supplementary position & navaidServicetype
information)*

The coded designator of a navaid is not always sufficient for
unambiguously referring to that element. The en-route navaids (VOR, DME,
NDB) designator is supposed to be unique (according to ICAO Annex 11)
within 600 NM. This means that these designators are not unique
world-wide. For airport navaids, there is no limitation.

FIXM adds two optional properties 'position' and 'navaidServiceType'
which may be used as a complement to the 'designator' information in
order to remove any ambiguity on the designator.

Important note: the combination of fields \[designator + position +
navaid service type\] shall not be interpreted as a natural key uniquely
identifying the navaid, in so far as producing and consuming
systems/services may use different aeronautical information sources with
different degree of precisions for lat/long, leading to small variations
of the position information. The supplementary fields shall be used for
disambiguation purposes only (i.e. plausibility checks based on position
and navaid service type) in case of duplicate/triplicate/…

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fb:navaid>
   <fb:designator>BOR</fb:designator>
   <fb:navaidServiceType>VOR_DME</fb:navaidServiceType>
   <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
      <fb:pos>52.36833333333333 -32.375</fb:pos>
   </fb:position>
</fb:navaid>
```

***

**OPTION 3 - Minimum reference with supplementary AIXM pointer**

*(OPTION 3 = OPTION 1 + supplementary hypertext reference)*

Option 3 corresponds to Option 1 with an additional hypertext reference
as described in chapter Generic hypertext references.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fb:navaid href="urn:uuid:08a1bbd5-ea70-4fe3-836a-ea9686349495">
   <fb:designator>BOR</fb:designator>
</fb:navaid>
```

***

**OPTION 4 - Complete reference**

*(OPTION 4 = OPTION 2 + OPTION 3)*

Option 4 corresponds to the combination of Option 2 and Option 3. See
explanations above.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fb:navaid href="urn:uuid:08a1bbd5-ea70-4fe3-836a-ea9686349495">
   <fb:designator>BOR</fb:designator>
   <fb:navaidServiceType>VOR_DME</fb:navaidServiceType>
   <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
      <fb:pos>52.36833333333333 -32.375</fb:pos>
   </fb:position>
</fb:navaid>
```