`GENERAL GUIDANCE`

`FIXM TYPE` [fb:SidStarReferenceType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_SidStarReferenceType.html#Link1E)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/SidStarReferenceType.png">

***

**OPTION 1 - Minimum reference**

The minimum SID or STAR reference shall consist of the SID or STAR
designator as published in the AIP.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:standardInstrumentDeparture>
   <fb:designator>AMOLO5B</fb:designator>
</fx:standardInstrumentDeparture>

```

***

**OPTION 2 - Minimum reference with supplementary AIXM pointer**

*(OPTION 2 = OPTION 1 + supplementary hypertext reference)*

Option 2 corresponds to Option 1 with an additional hypertext reference
as described in chapter Generic hypertext references.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:standardInstrumentDeparture href="urn:uuid:...">
   <fb:designator>AMOLO5B</fb:designator>
</fx:standardInstrumentDeparture>
```

***

**Abbreviated designators**

FIXM also supports the supplementary provision of the abbreviated
designator of the SID or the STAR which is commonly used in FMS
databases and in some ground automation systems. The ‘abbreviated
designator’, if provided, should be the designator obtained after
applying the rules for shortening names specified by the ARINC 424
specification, chapter 7.4. Example:

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:standardInstrumentDeparture>
   <fb:abbreviatedDesignator>AMOL5B</fb:abbreviatedDesignator>
   <fb:designator>AMOLO5B</fb:designator>
</fx:standardInstrumentDeparture>
```