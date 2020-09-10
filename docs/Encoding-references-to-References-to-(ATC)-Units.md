`GENERAL GUIDANCE`

`FIXM TYPE` [fb:AtcUnitReferenceType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_AtcUnitReferenceType.html#Link10)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/AtcUnitReferenceType.png">

***

**OPTION 1 - Minimum reference**

The minimum ATC unit reference shall consist of the location indicator
of the unit, if provided by ICAO Doc 7910 \[11\]. If the unit has no
ICAO Doc 7910 location indicator, the minimum airspace reference shall
consist of the name of the unit or any alternate name, as published in
the AIP.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

CASE 1 – The Unit has an ICAO Doc 7910 location indicator

```xml
<fx:originator>
   <fb:locationIndicator>EBBU</fb:locationIndicator>
</fx:originator>
```

CASE 2 – The Unit has no ICAO Doc. 7910 location indicator

```xml
<fx:originator>
   <fb:atcUnitNameOrAlternate>MILITARY DONLON TWR</fb:atcUnitNameOrAlternate>
</fx:originator>
```

***

**OPTION 2 - Minimum reference with supplementary AIXM pointer**

*(OPTION 2 = OPTION 1 + supplementary hypertext reference)*

Option 2 corresponds to Option 1 with an additional hypertext reference
as described in chapter Generic hypertext references.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

CASE 1 – The Unit has an ICAO Doc 7910 location indicator

```xml
<fx:originator href="urn:uuid:...">
   <fb:locationIndicator>EBBU</fb:locationIndicator>
</fx:originator>
```

CASE 2 – The Unit has no ICAO Doc. 7910 location indicator

```xml
<fx:originator href="urn:uuid:...">
   <fb:atcUnitNameOrAlternate>MILITARY DONLON TWR</fb:atcUnitNameOrAlternate>
</fx:originator>
```