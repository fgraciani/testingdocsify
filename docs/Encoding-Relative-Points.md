`GENERAL GUIDANCE`

`FIXM TYPE` [fb:RelativePointType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_RelativePointType.html#Link18)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/RelativePointType.png">

A relative point is a bearing and distance from a reference navaid.
Encoding a relative point in FIXM requires the ‘bearing’, ‘distance’ and
‘referencePoint’ properties to be provided. All of these properties
shall be provided.

FIXM enables a relative point to be supplemented with an optional
‘position’ value for storing the actual position of the relative point
if already known. The exchange of this information may prove useful in
order to save consuming systems / services from (re)computing the
position of the relative point. Whether or not to use this supplementary
information is at the discretion of the consuming system / service.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

Without position information

```xml
<fb:relativePoint>
   <fb:bearing uom="DEG" zeroBearingType="MAGNETIC_NORTH">82.0</fb:bearing>
   <fb:distance uom="NM">2.0</fb:distance>
   <fb:referencePoint>
      <fb:designator>BOR</fb:designator> (*)
   </fb:referencePoint>
</fb:relativePoint>
```

With position information

```xml
<fb:relativePoint>
   <fb:bearing uom="DEG" zeroBearingType="TRUE_NORTH">180</fb:bearing>
   <fb:distance uom="NM">60.0</fb:distance>
   <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
      <fb:pos>51.36833333333333 -32.375</fb:pos>
   </fb:position>
   <fb:referencePoint>
      <fb:designator>BOR</fb:designator> (*)
   </fb:referencePoint>
</fb:relativePoint>
```

(*) See chapter References to Navaid above. All four options can be used for encoding this reference. OPTION 1 is used in this example.
