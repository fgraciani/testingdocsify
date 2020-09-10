`GENERAL GUIDANCE`

`FIXM TYPE` [fb:DesignatedPointType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_DesignatedPointType.html#Link12)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/DesignatedPointType.png">

***

**OPTION 1 - Minimum reference**

As a minimum, the coded designator of waypoint shall be provided, as
published in the AIPs.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fb:designatedPoint>
   <fb:designator>TEMPO</fb:designator>
</fb:designatedPoint>
```

This is the minimum reference that SHALL be provided.

***

**OPTION 2 - Unambiguous reference**

*(OPTION 2 = OPTION 1 + supplementary position information)*

The coded designator of a waypoint is not always sufficient for
unambiguously referring to that element. The 5-letter coded designator
of a waypoint is supposed to be unique world-wide (according to ICAO
Annex 11) but is not in reality. There are at least 5%
duplicates/triplicates/even more…

FIXM adds an optional property 'position' which may be used as a
complement to the 'designator' information in order to remove any
ambiguity on the designator.

Important note: the combinations of fields \[designator + position\]
shall not be interpreted as a natural key uniquely identifying the
waypoint, in so far as producing and consuming systems/services may use
different aeronautical information sources with different degree of
precisions for lat/long, leading to small variations of the position
information. The supplementary fields shall be used for disambiguation
purposes only (i.e. plausibility checks based on position) in case of
duplicate/triplicate/…

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fb:designatedPoint>
   <fb:designator>TEMPO</fb:designator>
   <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
      <fb:pos>56.84 -29.860000000000003</fb:pos>
   </fb:position>
</fb:designatedPoint>
```

***

**OPTION 3 - Minimum reference with supplementary AIXM pointer**

*(OPTION 3 = OPTION 1 + supplementary hypertext reference)*

Option 3 corresponds to Option 1 with an additional hypertext reference
as described in chapter Generic hypertext references.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fb:designatedPoint href="urn:uuid:81e47548-9f00-4970-b641-8ff8f99098a5">
   <fb:designator>TEMPO</fb:designator>
</fb:designatedPoint>
```

***

**OPTION 4 - Complete reference**

*(OPTION 4 = OPTION 2 + OPTION 3)*

Option 4 corresponds to the combination of Option 2 and Option 3. See
explanations above.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fb:designatedPoint href="urn:uuid:81e47548-9f00-4970-b641-8ff8f99098a5">
   <fb:designator>TEMPO</fb:designator>
   <fb:position srsName="urn:ogc:def:crs:EPSG::4326">
      <fb:pos>56.84 -29.860000000000003</fb:pos>
   </fb:position>
</fb:designatedPoint>
```

***

**Note about the pattern constraint for waypoint designators**

FIXM supports waypoint designators of 1 to 5 characters. This design is
intentional. In most cases, waypoints have a 5-letter designator, as
prescribed by ICAO. However, these designators might be shorter in some
particular cases. Examples of shorter waypoint designators could be
found in various sources:

-   In chapter 7 of the ARINC 424 specification. This chapter provides
    rules for forming the designators of waypoints in the absence of
    published designators. These rules can lead to designators of less
    than 5 characters. The following extracts from ARINC 424-19 provide
    some examples, which are highlighted in blue.

> Examples:
> 
> 3.0 NM from DOOTY should be expressed as <span style="color:blue">**3NM**</span>.
>
> 2.8 NM from CHASS should be expressed as <span style="color:blue">**28NM**</span>.
>
> 11.0 NM from BACUP should be expressed as <span style="color:blue">**NM11**</span>.
>
> 11.0 NM from BACUP should be expressed as <span style="color:blue">**NM11**</span>.
>
> 11.0 NM from KITTY should be expressed as <span style="color:blue">**NM138**</span>.

> |Fix Ident|Fix Name|
> |:--|:--|
> |<span style="color:blue">**AB13**</span>|AB180013 AB 180.3 degrees 12.8|

-   In the [US FAA’s publication of Instrument Flight Procedures
    encodings in ARINC 424-18
    format](https://www.faa.gov/air_traffic/flight_info/aeronav/digital_products/cifp/download/).
    For instance:

Localizer only approach on RWY06 at KFOD

> SUSAP KFODK3FL06 AFOD 010FOD K3D 0V IF 18000 0 NS 854081209
>
> SUSAP KFODK3FL06 AFOD 020<span style="color:blue">**FF06**</span> K3PC0E TF + 02800 0 NS 854091209
>
> SUSAP KFODK3FL06 AFOD 030<span style="color:blue">**FF06**</span> K3PC0EE AR PI IFODK3 2430006119800100PI + 02800 0 NS 854101209
>
> SUSAP KFODK3FL06 AHIMSU 010HIMSUK3PC0E A IF FOD K3 15000140 D 18000 0 NS 854111310
>
> SUSAP KFODK3FL06 AHIMSU 020SHRLAK3PC0EE BR AF FOD K3 216501401500 D + 02800 0 NS 854121310
>
> SUSAP KFODK3FL06 ALESFI 010LESFIK3PC0E A IF FOD K3 25400140 D 18000 0 NS 854131310
>
> SUSAP KFODK3FL06 ALESFI 020SHRLAK3PC0EE BL AF FOD K3 216501402540 D + 02800 0 NS 854141310
>
> SUSAP KFODK3FL06 L 010SHRLAK3PC0E I IF IFODK3 24300163 PI + 02800 18000 0 NS 854151310
>
> SUSAP KFODK3FL06 L 020<span style="color:blue">**FF06**</span> K3PC0E F CF IFODK3 2430006106300101PI + 02800 FO K3PN0 NS 854161209
>
> SUSAP KFODK3FL06 L 021ATLOJK3PC0E S CF IFODK3 2430003406300028PI + 01820 -324 0 NS 854171310
>
> SUSAP KFODK3FL06 L 030RW06 K3PG0GY M CF IFODK3 2430001306300021PI 01134 -324 0 NS 854181209
>
> SUSAP KFODK3FL06 L 040 0 M CA 0630 + 02800 0 NS 854191209
>
> SUSAP KFODK3FL06 L 050FOD K3D 0VY L DF + 02800 0 NS 854201209
>
> SUSAP KFODK3FL06 L 060FOD K3D 0VE R HM 1204T010 + 02800 0 NS 854211209

GPS approach on RWY29 at KFOT

> SUSAP KFOTK2FP29 ADINSE 010DINSEK2EA0E A IF 18000 P PS 857251211
>
> SUSAP KFOTK2FP29 ADINSE 020JEWPEK2PC0E TF + 06000 P PS 857261310
>
> SUSAP KFOTK2FP29 ADINSE 030SPHERK2PC0EE TF + 04700 P PS 857271310
>
> SUSAP KFOTK2FP29 AKNEES 010KNEESK2EA0E IF 18000 P PS 857281211
>
> SUSAP KFOTK2FP29 AKNEES 020YAGERK2EA0E A TF + 06800 P PS 857291211
>
> SUSAP KFOTK2FP29 AKNEES 030SPHERK2PC0EE TF + 04700 P PS 857301310
>
> SUSAP KFOTK2FP29 APLYAT 010PLYATK2EA0E A IF 18000 P PS 857311211
>
> SUSAP KFOTK2FP29 APLYAT 020JEVGYK2PC0E TF + 06000 P PS 857321310
>
> SUSAP KFOTK2FP29 APLYAT 030SPHERK2PC0EE TF + 04700 P PS 857331310
>
> SUSAP KFOTK2FP29 P 010SPHERK2PC0E I IF + 04700 18000 P PS 857341310
>
> SUSAP KFOTK2FP29 P 011JEVSYK2PC0E S TF + 03700 P PS 857351310
>
> SUSAP KFOTK2FP29 P 020ELLYSK2PC0E F TF + 02700 IZPUH K2PCP PS 857361310
>
> SUSAP KFOTK2FP29 P 021<span style="color:blue">**SP29**</span> K2PC0E A TF + 01840 -356 P PS 857371211
>
> SUSAP KFOTK2FP29 P 030IZPUHK2PC0EY M TF 00617 -356 P PS 857381310
>
> SUSAP KFOTK2FP29 P 040 0 M CA 2757 + 01500 P PS 857391211
>
> SUSAP KFOTK2FP29 P 050FOT K2D 0VY R DF + 03000 P PS 857401211
>
> SUSAP KFOTK2FP29 P 060FOT K2D 0VE R HM 1610T010 + 03000 P PS 857411510

-   In the European AIS Database (EAD). A query on the EAD helped
    identify the following:

    -   40 occurrences of designated points with a 1-letter designator

    -   190 occurrences of designated points with a 2-letters designator

    -   356 occurrences of designated points with a 3-letters designator

    -   3046 occurrences of designated points with a 4-letters
        designator

 Most of the designated points with 2, 3 or 4-letter designators
 actually correspond to designated points formed after the position of
 a navaid or an aerodrome. However, some occurrences cannot be related
 to these cases. The following table quotes a few random examples.

| **Designator**        | **Lat**      | **Long**      | **Type** |
|-----------------------|--------------|---------------|----------|
| *1-letter designator* |              |               |          |
| N                     | 503241N      | 0042718E      | ADHP     |
| E                     | 502941N      | 0044206E      | ADHP     |
| A                     | 475826.0000N | 0161445.0000E | OTHER    |
| B                     | 475202.0000N | 0161514.0000E | OTHER    |
| B                     | 475734.0000N | 0161614.0000E | OTHER    |
| *2-letter designator* |              |               |          |
| S1                    | 460217N      | 0142702E      | OTHER    |
| S2                    | 460552N      | 0142748E      | OTHER    |
| S3                    | 460845N      | 0142452E      | OTHER    |
| W1                    | 461846N      | 0141449E      | OTHER    |
| W2                    | 461744N      | 0142049E      | OTHER    |
| A1                    | 453243N      | 0181709E      | OTHER    |
| A2                    | 423842N      | 0175651E      | ADHP     |
| A3                    | 434049N      | 0155502E      | ADHP     |
| *3-letter designator* |              |               |          |
| PJ1                   | 544005N      | 0253057E      | OTHER    |
| PJ2                   | 554243N      | 0211434E      | OTHER    |
| PJ3                   | 561350N      | 0221534E      | OTHER    |
| TP1                   | 481018.5959N | 0113540.1135E | ADHP     |
| TP2                   | 481314.6479N | 0113003.5398E | ADHP     |
| 13A                   | 512900.0000N | 0185100.0000E | OTHER    |
| 17A                   | 520800.0000N | 0174500.0000E | OTHER    |
| 20A                   | 514400.0000N | 0160800.0000E | OTHER    |
| 21A                   | 521300.0000N | 0162800.0000E | OTHER    |
| 27A                   | 523500.0000N | 0160500.0000E | OTHER    |
| ME1                   | 462338N      | 0155433E      | OTHER    |
| ME2                   | 463440N      | 0155009E      | OTHER    |
| DX1                   | 481323.7979N | 0122604.5443E | ADHP     |
| DX1                   | 505951.6149N | 0141519.3372E | ADHP     |
| DX2                   | 505625.7259N | 0141418.8105E | ADHP     |
| *4-letter designator* |              |               |          |
| SJ91                  | 000224S      | 1044205E      | OTHER    |
| FF36                  | 375713.7253S | 1751802.2481E | ADHP     |
| SM01                  | 464002.55N   | 0170535.52E   | ADHP     |
| SM02                  | 464750.28N   | 0165926.87E   | ADHP     |
| LDD5                  | 514138.7284N | 0191615.9435E | ADHP     |
| PG23                  | 545132N      | 0230742E      | OTHER    |
| IF09                  | 431021.1N    | 0252819.1E    | ADHP     |
| MAPT                  | 492818.3679N | 0083229.2734E | ADHP     |
| SDF2                  | 495218.7277N | 0112216.9347E | ADHP     |
| FF16                  | 513503.7055N | 1124320.1363W | ADHP     |
| ECHO                  | 504818N      | 0051950E      | ADHP     |
| ECHO                  | 482129.75N   | 0703422.93W   | OTHER    |
