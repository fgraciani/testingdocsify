`GENERAL GUIDANCE`

`FIXM TYPE` [fb:TimeType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_TimeType.html#LinkA6)

FIXM requires times to be expressed in UTC.

A constraint is placed on class *Base.Types.Time*, the class used to
represent all date/time values in FIXM, imposes the use of the trailing
character ‘z’ to indicate UTC, in line with the W3C XSD specification.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

20th July 1969 at 20:18UTC is expressed as 1969-07-20T20:18:00.000Z

***

**Note to implementers**

The mapping of the XSD type dateTime to native structures in various
development contexts is not always 1-1 and may exhibit a wide variety of
difficulties depending on the tooling and runtime context. In
particular, the trailing character ‘z’ indicating UTC may actually be
stripped/omitted, leading to FIXM times being interpreted as local times
instead of UTC times by some applications. FIXM implementers are
therefore invited to crosscheck that their systems correctly interpret
FIXM times as UTC time.