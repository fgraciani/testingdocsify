`GENERAL GUIDANCE`

`FIXM TYPE` [fb:RunwayDirectionDesignatorType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_RunwayDirectionDesignatorType.html#Link1C)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/RunwayDirectionDesignatorType.png">

***

**OPTION 1 - Minimum reference**

The minimum Runway Direction reference shall consist of the Runway
Direction designator.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:runwayDirection>09L</fx:runwayDirection>
```

***

**OPTION 2 - Minimum reference with supplementary AIXM pointer**

*(OPTION 2 = OPTION 1 + supplementary hypertext reference)*

Option 2 corresponds to Option 1 with an additional hypertext reference
as described in chapter Generic hypertext references.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:runwayDirection href="urn:uuid:c8455a6b-9319-4bb7-b797-08e644342d64">09L</fx:runwayDirection>
```