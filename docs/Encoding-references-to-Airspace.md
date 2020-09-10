`GENERAL GUIDANCE`

`FIXM TYPE` [fb:AirspaceDesignatorType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_AirspaceDesignatorType.html#LinkE)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/AirspaceDesignatorType.png">

***

**OPTION 1 - Minimum reference**

The minimum airspace reference shall consist of the airspace location
indicator, if provided by ICAO Doc 7910 \[11\]. If the airspace has no
ICAO Doc 7910 location indicator, the minimum airspace reference shall
consist of the coded designator of the airspace as published in the AIP.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

CASE 1 – The Airspace has an ICAO Doc 7910 location indicator

```xml
   <fx:region>KZLC</fx:region>
```

CASE 2 – The Airspace has no ICAO Doc. 7910 location indicator

```xml
<fx:region>AMSWELL</fx:region>
```

***

**OPTION 2 - Minimum reference with supplementary AIXM pointer**

*(OPTION 2 = OPTION 1 + supplementary hypertext reference)*

Option 2 corresponds to Option 1 with an additional hypertext reference
as described in chapter Generic hypertext references.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

CASE 1 – The Airspace has an ICAO Doc 7910 location indicator

```xml
<fx:region href="urn:uuid:...">KZLC</fx:region>
```

CASE 2 – The Airspace has no ICAO Doc. 7910 location indicator

```xml
<fx:region href="urn:uuid:...">AMSWELL</fx:region>
```
