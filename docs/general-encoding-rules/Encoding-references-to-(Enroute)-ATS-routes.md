`GENERAL GUIDANCE`

`FIXM TYPE` [fb:RouteDesignatorType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_RouteDesignatorType.html#Link1A)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/RouteDesignatorType.png">

***

**OPTION 1 - Minimum reference**

The minimum Enroute ATS Route reference shall consist of the Enroute ATS
Route designator as published in the AIP. Enroute ATS Route designators
are not unique. However, the systematic pairing of an ATS route
designator with a route point (i.e. a significant point belonging to
that ATS route) in FIXM is considered sufficient for enabling
unambiguous identification of the ATS Route being referred to.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:routeDesignator>UA4</fx:routeDesignator>
```

***

**OPTION 2 - Minimum reference with supplementary AIXM pointer**

*(OPTION 2 = OPTION 1 + supplementary hypertext reference)*

Option 2 corresponds to Option 1 with an additional hypertext reference
as described in chapter Generic hypertext references.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:routeDesignator href="urn:uuid:a14a8751-5428-46bc-a2d1-32ef84d37b5c">UA4</fx:routeDesignator>
```