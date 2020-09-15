`GENERAL GUIDANCE`

# What is a FIXM Application?

An **Application Library** is a FIXM component that addresses the use of
FIXM Core in a given context. It can be of global, regional or local
applicability, depending on the context. An **Application Library**
essentially provides context-specific **‘message data structures’** and
**‘message templates’** which enables harmonized representation of the
FIXM-based messages exchanged using SWIM information services, as
outlined in the figure below.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/message_structure_fixm_application_role.png"/>

*Figure: General structure of a message and role of an Application Library*

An **Application Library** captures messaging related data elements and
reuses and restricts relevant subsets of the FIXM Core data structures.
FIXM Core is independent and does not require an update when changes in
an application library occur.

An **Application Library** may also leverage **Extensions**, as illustrated on the picture below:

<img src="https://github.com/hlepori/fixm_test/blob/master/media/fixm_application_with_extension.png" />


An example of an Application Library is the **FF-ICE Application
Library** developed and released by the FIXM CCB. This library addresses
the use of FIXM core in the specific context of FF-ICE. It provides
harmonized FF-ICE Message data structure (e.g. data structures for
representing the FF-ICE Filing Status, the FF-ICE Planning Status etc.)
and the FF-ICE message templates (e.g. the template for the FF-ICE Filed
Flight Plan Message, the template for the FF-ICE Flight Cancellation
Message etc.), in line with the FF-ICE Implementation Guidance Manual.

More details about this FF-ICE Application Library can be found in
Chapter 3.2 .

## Message Data Structures

Message Data structures designate at high level the data structures that
are necessary for understanding the meaning and purpose of the
information that is exchanged in a given context. They commonly include
message identifiers and timestamps, codes identifying business types of
messages, and any context-specific data that qualify the associated
message interactions[2].

Examples of message data structures can be found in the FF-ICE
Implementation Guidance Manual. The Figure below shows the message data
structures associated with the FF-ICE Flight Cancellation Message.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/ffice_message_data_example.png" />

*Figure 2: Example of Message Data structures from FF-ICE*

## Message Templates

A message template is a more restrictive subset of message and flight
data structures that is relevant to a given information exchange. In
SWIM terms, a message template provides guidance for formatting a given
information service payload.

By removing unused fields, adjusting multiplicities, and adding or
further limiting pattern constraints, a template can tailor the broad
standard represented by FIXM to reflect the content requirements of a
particular message exchange. Templates offer message-specific guidance
and validation rules while remaining entirely compliant with the broader
FIXM structures.

A list of benefits for employing templates is detailed below.

| **Benefit of templates** | **Without templates** | **With templates**    |
|:-------------------------|:----------------------|-----------------------|
| Reduced Development Overhead | Increased development overhead as each user must independently interpret how message content requirements should be represented in FIXM format. | Tailored schemas reduce development overhead by providing additional guidance for creating messages with a FIXM-based content. |
| Consistent Message Structure | Individual interpretations of requirements could lead to inconsistent message content implementation across users.                                                                           | Making dedicated implementation templates available to all users should improve implementation consistency.                    |
| Improved XML Validation      | XML-based validation limited to data syntax checking with no guidance for required vs. optional or allowed vs. not allowed content (failing to fully leverage a major benefit of using XML). | XML-based validation enforces both syntax and content completeness rules (fully leveraging benefits of XML-based validation).  |

The use of message templates therefore improves interoperability, data
quality, and ease and cost of development for any exchange they are
applied to. They provide FIXM users with guidance and structure while at
the same time allowing FIXM to remain open and flexible.

**XML representation of FIXM-based Message Templates**

The XML representation of FIXM-based Message templates is currently
achieved by restricting complex types defined by FIXM. Restricting
complex types is a standard-based approach for removing unwanted
elements and/or attributes and to apply tighter restraints to
multiplicities, patterns, and facets. Complex type restrictions also
provide built-in validation: if the restriction is not correctly formed
in relation to the parent type then the resulting schemas will not
validate.

**Benefits of XSD restrictions**

-   XSD restrictions are explicit: using an XSD schema with restrictions
    means using the rules of the base XSD schema plus additional rules
    that are explicitly declared;

-   XSD restrictions provide some built-in validation for quality
    assurance

-   XSD restrictions represent a natural use of the XSD standard;

-   XSD restrictions deliver benefits in terms of model development and
    maintenance. [3]

**Potential shortcomings of XSD restrictions**

The online literature about XML schema design generally considers that
the restrictions of XSD complex types are the most difficult and
therefore the least supported part of the XML schema specification.
Implementers experiencing issues with the FIXM templates are invited to
report their problems to the FIXM community, with details about the
development environment being used. Alternatives to XSD restrictions may
be then considered, as appropriate (see next section).

**XSD Profiles as a potential alternative to XSD Restrictions**

An XSD profile would represent a reduced, further restricted subset of
the original model. This approach is very similar to using restrictions
but accomplishes the task by directly creating smaller, parallel models
of the adjusted packages rather than producing them via a restriction.
The figure below illustrates at high-level the differences.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/xsd_restriction_vs_xsd_profile.png"/>

*Figure: XSD Restriction vs XSD Profile*

XSD profiles would not restrict the types from the base reference and
would not bring any additional complexity. They could therefore be
processed by marshalling tools in a smoother way compared to XSD
restrictions.

XSD profiles may be therefore developed as an alternative to XSD
restrictions for representing FIXM-based message templates.

## How to build an application library?

APPENDIX B provides detailed guidance for creating application
libraries.