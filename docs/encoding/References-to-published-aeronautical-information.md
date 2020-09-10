Describing the predicted movement of a flight commonly means indicating
which parts of the infrastructure (ATS routes, waypoints, radio
navigation aids etc.) are expected to be used by the flight. This is
enabled in FIXM by a set of “references” constructs. These references
are not flight-specific information; they pertain to the aeronautical
information domain.

Different formats exist for exchanging aeronautical information, whose
usages depend on specific implementation considerations and actual
context within the overall data chain. For instance:

-   AIXM is developed in order to enable the provision in digital format
    of the aeronautical information that is in the scope of Aeronautical
    Information Services (AIS). AIXM 5.1 covers both the content of
    Aeronautical Information Publications (AIP) and of the NOTAM
    information.

-   The ARINC 424 standard defines a format for navigation (and
    communication) information, including but not limited to, aerodrome,
    runway, navaid, airway and terminal approach procedure information
    that is exchanged between data suppliers and avionics vendors.

-   The Aerodrome Mapping Exchange Schema (AMXM XML Schema) is an
    exchange format specification for AMDB as standardized by and
    dedicated to the EUROCAE/RTCA Aeronautical Databases WG44/SC217. It
    is an XML Schema implementation of the DO-291C/ED-119C AMXM UML
    model.

**FIXM does not import any of these formats or profiles thereof.** FIXM
defines its own structures for referring to aeronautical information
that are **self-contained** but mappable to their AIXM/AMXM… equivalents
thanks to the reuse of a common semantics. FIXM also provides an
**optional** mechanism enabling these self-contained references to be
supplemented with, but not replaced by, **hypertext** **references** to
AIXM features.

The following pages provide guidance for correctly encoding these
references in FIXM.
- ...
