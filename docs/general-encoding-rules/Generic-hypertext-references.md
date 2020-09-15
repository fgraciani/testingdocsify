`GENERAL GUIDANCE`

If an AIXM 5.1 feature exists that corresponds to the element being
referred to, an **optional** hypertext reference to that AIXM feature
may be provided. This reference shall be expressed in accordance with
chapter 3.4.1 (*Abstract references using UUID*) of the [AIXM feature
Identification and
Reference](http://www.aixm.aero/sites/aixm.aero/files/imce/AIXM51/aixm_feature_identification_and_reference-1.0.pdf)
document developed by the AIXM community.

This hypertext reference may be used - or ignored - by the receiving
system depending on its capabilities.

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

```xml
<fx:*\[FIXMelement\]* href="urn:uuid:81e47548-9f00-4970-b641-8ff8f99098a5">
```

Important note: FIXM does not import the W3C XML Linking Language
(xlink) v1.1 schemas in order to represent the hypertext references.
FIXM mimics the xlink Locator attribute named “href” but defines it
within the FIXM (Base) namespace[5].