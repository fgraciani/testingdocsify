`FF-ICE GUIDANCE`

The FF-ICE Application Library is an Application Library[7] for FIXM
that addresses the specific use of FIXM Core in the context of ICAO
FF-ICE. It provides harmonized FF-ICE Message data structures and the
individual FF-ICE Message templates in line with the requirements on
FF-ICE Messages defined by the ICAO FF-ICE Implementation Guidance
Manual (ICAO Doc 9965 Volume II).

The content of the FF-ICE Application Library is the following:

<img src="https://github.com/hlepori/fixm_test/blob/master/media/overview_ffice_application.png" />

*Figure: Overview of the FF-ICE Message Application Library content*

The FF-ICE Message Application Library is developed and published by the
FIXM CCB, together with FIXM Core.

***

**FF-ICE Message data structures**

The FF-ICE message data structures are the data elements that
specifically qualify the FF-ICE Messages. They do not describe a Flight
but are necessary for understanding the purpose and meaning of an FF-ICE
information exchange. The FF-ICE message data modelled by the FF-ICE
Application Library include:

-   A model element representing generically an FF-ICE Message with its
    identifier, timestamp, type etc. An enumeration provides the
    possible types of FF-ICE Messages: Filed Flight Plan message,
    Submission Response message, Filing Status message etc.

-   Model elements representing the different FF-ICE statuses with their
    possible values: Planning statuses CONCUR / NON\_CONCUR / NEGOTIATE,
    Filing statuses ACCEPTABLE / NOT\_ACCEPTABLE, Submission statuses
    ACK / MANUAL / REJECT etc.

-   Model elements representing the FF-ICE participants and their
    properties, which are used for identifying the operational
    stakeholders sending and receiving FF-ICE messages, or the list of
    relevant ASPs etc.

The FF-ICE Message data structures are traceable to the FF-ICE
Implementation Guidance Manual Appendix B. For instance:

<img src="https://github.com/hlepori/fixm_test/blob/master/media/example_ffice_message_data_to_ffice_ig_appB_trace.png" />

*Figure: Example of FF-ICE Message data structures tracing to the FF-ICE Implementation Guidance Manual, Appendix B*

The FF-ICE message data structures other than Choices and Codelists are
extendable. This enables implementers to accommodate additional FF-ICE
message data structures required locally or regionally, in support of
local or regional FF-ICE requirements. Extension hooks are defined in a
similar fashion as for FIXM Core data structures.

The picture below provides an overview of the FF-ICE Message data
structures modelled in the FF-ICE Application Library.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/ffice_message_data_structures_overview.png" />

*Figure 9: Overview of the FF-ICE Message Data Structures*

***

**FF-ICE Message Templates**

The FF-ICE Message templates are the representations of the individual
FF-ICE messages that are exchanged by the FF-ICE Services. Thirteen
message templates are defined in the FF-ICE Application library v1.0.0.
They correspond to the thirteen FF-ICE Messages described in the
FF-ICE/R1 Implementation Guidance Manual, Appendix C. The following
table provides the correspondence between the FF-ICE message templates
from the library and their corresponding description in the FF-ICE
Implementation Guidance Manual, Appendix C.

*Table: Correspondences between FF-ICE Message templates and their ICAO Doc 9965 Volume II description*

| **FF-ICE Message templates** | **Associated Requirements from the FF-ICE Implementation Guidance Manual, Appendix C** |
|:-----------------------------|:---------------------------------------------------------------------------------------|
| FiledFlightPlan              | C-4 Filed Flight Plan                                                                  |
| FilingStatus                 | C-5 Filing Status                                                                      |
| FlightArrival                | C-13 Flight Arrival                                                                    |
| FlightCancellation           | C-8 Flight Cancellation                                                                |
| FlightDataRequest            | C-10 Flight Data Request                                                               |
| FlightDataResponse           | C-11 Flight Data Response                                                              |
| FlightDeparture              | C-12 Flight Departure                                                                  |
| FlightPlanUpdate             | C-9 Flight Plan Update                                                                 |
| PlanningStatus               | C-3 Planning Status                                                                    |
| PreliminaryFlightPlan        | C-2 Preliminary Flight Plan                                                            |
| SubmissionResponse           | C-1 Submission Response                                                                |
| TrialRequest                 | C-6 Trial Request                                                                      |
| TrialResponse                | C-7 Trial Response                                                                     |

The FF-ICE Message templates define concretely the restricted subsets of
the FF-ICE Message data elements of the FIXM Core flight elements that
are relevant for each FF-ICE message transaction. They explicitly
declare which elements are mandatory, optional or irrelevant in each
case, and enforce stricter content patterns as appropriate.

***

**Example of the FF-ICE ‘Flight Cancellation’ Message**

The following table is a simplified version of table C-8 from the FF-ICE
Implementation Guidance Manual, Appendix C. It describes the content of
the FF-ICE Flight Cancellation Message and indicates which fields are
mandatory (highlighted **in bold** in this document) or optional
(highlighted in *in italic*).

*Table: Example of the FF-ICE Flight Cancellation Message*

<img src="https://github.com/hlepori/fixm_test/blob/master/media/example_ffice_flight_cancellation_message.png" />

The FF-ICE Application library translates this table into an
implementable message template. This is illustrated by the picture
below. The message template resulting from the translation of this table
is displayed with a blue background.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/ffice_flight_cancellation_template.png" />

*Figure 10: The FF-ICE Flight Cancellation Message Template*

**Explanations**

**XSD complex type restrictions** are used to pare down the Flight and
the FF-ICE Message data structures to just those fields that are
applicable to the Flight Cancellation Message, as well as to enforce
stricter optionality and content patterns where appropriate.

The XSD complex type restrictions are implemented by creating a new
class that generalizes the class to be restricted and then applying the
&lt;&lt;XSDrestriction&gt;&gt; stereotype to the generalization
connector, as shown in brown on the picture opposite.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/example_xsd_complex_type_restrictions_1.png"/>

XML elements being irrelevant in the context of the message template are
eliminated by removing them from the model, as shown in red on the
picture opposite. Elements being mandatory in the context of the message
template have their cardinality set to (at least) 1 in the restriction,
as shown in blue.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/example_xsd_complex_type_restrictions_2.png"/>

In general, all optionality, cardinality, and pattern restrictions are
implemented by applying the desired changes to the restricted class.

Because XSD complex type restrictions must use the same namespace as the
types they restrict, it is necessary to change their names. The
convention used in the FF-ICE Application Library is to prepend each
restricted class with “Ffice” plus an initialism of the message being
modeled – hence **FficeFC** for the FF-ICE **<u>F</u>**light
**<u>C</u>**ancellation Message.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/example_xsd_complex_type_restrictions_3.png"/>

Restricted classes require the restricted versions of associated
sub-classes. XSD complex type restrictions are therefore linked together
to form an entire restricted message. This provides clear guidance on
how the FF-ICE message template is constructed.

<img src="https://github.com/hlepori/fixm_test/blob/master/media/example_xsd_complex_type_restrictions_4.png"/>