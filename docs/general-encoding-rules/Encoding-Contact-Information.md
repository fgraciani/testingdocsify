`GENERAL GUIDANCE`

`FIXM TYPE` [fb:ContactInformationType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_ContactInformationType.html#Link1)

<img src="https://github.com/hlepori/fixm_test/blob/master/media/ContactInformationType.png"/>

***

**Postal Address** <a id="postal_address"></a>

> TODO

***

**Telephone Contact** <a id="telephone_contact"></a>

> TODO

***

**Online Contact**

`FIXM TYPE` [fb:OnlineContactType](https://www.fixm.aero/releases/FIXM-4.2.0/doc/schema_documentation/Fixm_ContactInformationType.html#Link1)

In FIXM, the online contact information can include an email address
and/or a network address.

A network address is always formed of two pieces of information: the
**linkage** and the **network** information.

-   The former captures the expression of the network address. This is
    supported by property OnlineContact.linkage.

-   The latter captures the network on which the address is valid. This
    is supported by property OnlineContact.network.

Property OnlineContact.network provides a choice between predefined
network types and free text. Network information should be preferably
encoded using the property NetworkChoice.**type** populated with the
applicable enumerated value from enumeration TelecomNetworkType. If none
of the enumerated values is suitable, the property NetworkChoice.other
shall be used. The ATM Information Reference Model provides additional
telecom network types that should be used for populating
NetworkChoice.other, as appropriate. These additional AIRM values are
available at the following link:

<http://airm.aero/viewer/1.0.0/logical-model.html#CodeTelecomNetworkType>

The type of network affects the format of the linkage information.

-   When the network is INTERNET, the linkage should be a resolvable URL

-   When the network is AFTN, the linkage should be a valid AFTN address

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

The following example illustrates contact information formed of an email
address and an Internet address expressed as a resolvable URL.

```xml
<fb:onlineContact>
   <fb:email>fixm.secretariat@eurocontrol.int</fb:email>
   <fb:linkage>https://www.fixm.aero/content/contact.pl</fb:linkage>
   <fb:network>
      <fb:type>INTERNET</fb:type>
   </fb:network>
</fb:onlineContact>
```

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

The following example illustrates contact information formed of an AFTN
address. The example features the EUROCONTROL NM ‘AFTN address’ for
Flight Plan Message Submission to IFPS (FP1 - Brussels (Haren)).

```xml
<fb:onlineContact>
  <fb:linkage>EUCHZMFP</fb:linkage>
  <fb:network>
     <fb:type>AFTN</fb:type>
  </fb:network>
</fb:onlineContact>
```

`EXAMPLE` <img src="https://github.com/hlepori/fixm_test/blob/master/media/ok.png" width="20" height="20" />

The following example illustrates contact information formed of a SITA
address. ‘SITA’ is not a value captured in FIXM enumeration
TelecomNetworkType but is part of the reference ATM vocabulary provided
by the AIRM ([AIRM codelist
CodeTelecomNetworkType](http://airm.aero/viewer/1.0.0/logical-model.html#CodeTelecomNetworkType)).
The example features the EUROCONTROL NM ‘SITA address’ for Flight Plan
Message Submission to IFPS (FP1 - Brussels (Haren)).

```xml
<fb:onlineContact>
   <fb:linkage>BRUEP7X</fb:linkage>
   <fb:network>
      <fb:other>SITA</fb:other>
   </fb:network>
</fb:onlineContact>
```