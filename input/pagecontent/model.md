<!-- Updates based on Jira tickets 
Date             Jira ticket        Updated by                   Comment
2023-06-16       OTHER-2411         Joanie Harper                Added closing parentheses per the Jira ticket https://jira.hl7.org/browse/OTHER-2411
2023-06-16       OTHER-2586         Joanie Harper                Change field name from Jurisdiction to Issuer, added **Definition**, and put Cardinality on its own
                                                                   line per https://jira.hl7.org/browse/OTHER-2586
2023-06-16       OTHER-2587         Joanie Harper                update Source Field Name and Source Field Desription per Jira ticket https://jira.hl7.org/browse/OTHER-2587
2023-06-16       OTHER-2575         Joanie Harper                Added hyphens per Jira ticket https://jira.hl7.org/browse/OTHER-2575
2023-06-16       OTHER-2578         Joanie Harper                Updated SPCU section per Jira ticket https://jira.hl7.org/browse/OTHER-2578
2023-06-23       OTHER-2671         Rob McClure                  Changed all to SPCU or Sex Parameter for Clinical Use
2023-07-13       OTHER-2463         Cooper Thompson              Updated RSG model definition and other narrative
2023-07-13       V2-25452           Cooper Thompson              Removed international equivalent references
2023-07-17       OTHER-2557         Cooper Thompson              Clarified terminology expectations for RSG
2023-07-25		  OTHER-2708	    	Carol Macumber		 	     	  GI Usage Note change per OTHER-2708
2023-07-25       OTHER-2539	    	Carol Macumber		 		     GI Usage Note change per OTHER-2539
2023-07-26		  OTHER-2570			Carol Macumber				     Standardized the use of "Gender Harmony initial informative specification"  when referring to initial 
                                                                  specification
2023-08-08       OTHER-2577         Joanie Harper                update text per Jira ticket 
2023-08-08       OTHER-2585         Joanie Harper                update text per Jira ticket 
2023-08-08       OTHER-2420         Joanie Harper                update text per Jira ticket 
2023-08-08       OTHER-2625         Joanie Harper                removed sentence per Jira ticket 
2023-08-08       OTHER-2582         Joanie Harper                update text per Jira ticket 
2023-08-08       OTHER-2581         Joanie Harper                update text per Jira ticket 
2023-08-08       OTHER-2494         Joanie Harper                update text per Jira ticket 
2023-08-08       OTHER-2540         Joanie Harper                add links for minValueSets per Jira ticket 
2023-08-08       OTHER-2576         Joanie Harper                update text per Jira ticket 
2023-08-14       OTHER-2709         Joanie Harper                update text per Jira ticket 
2023-08-22       OTHER-2532         Rob McClure                  Clarify use of "sex or gender"
2023-08-22        various           Rob McClure                  Updated RSG description and Usage Notes to clarify that SAAB (and Administrative Gender) can be directly exchanged without "wrapping" in RSG template and as such they should be considered a conformant exchange of USCDI v4 "Sex"
2023-08-22        OTHER-2512        Rob McClure                  Confirmed removal of ICAO element and added explanation of change.
2023-08-22        OTHER-2589        Rob McClure                  Added section noting changes in the model when compared to original. Confirmed changes in bindings. provided links to binding strength definitions.
2023-08-28       OTHER-2569         Joanie Harper                update per Jira ticket -- still need links to V2 spec and CDA spec
2023-08-28       OTHER-2580         Joanie Harper                update Gender Harmony capitalization

-->

### Modeling Sex and Gender Representation

The World Health Organization (WHO) defines Sex as the "different
biological and physiological characteristics of males and females, such
as reproductive organs, chromosomes, hormones, etcetera" and Gender as
the "socially constructed characteristics of women and men, such as
norms, roles, and relationships of and between groups of women and men"
(WHO, 2020.) In clinical practice however, there can be a multiplicity
of contextual variants over a single time horizon, across multiple
applications and/or institutions where clinicians, vendors and interface
developers have been grappling to create their own electronic 'work
around' specification(s) to meet local and/or internal needs.

The gender-marginalized community has health care requirements that
demand improvements that will benefit all patients. This implementation
guide provides structural and semantic guidance to vendors and interface
developers to address these requirements.

The [HL7 Informative Document: Gender Harmony - Modeling Sex and Gender Representation, Release 1](http://www.hl7.org/implement/standards/product_brief.cfm?product_id=564)  provides necessary constructs to more
accurately capture sex and gender identity along with associated context of use.
While the framework provides the necessary infrastructure, the specific
changes in individual standards to concretely specify actual implementable 
structures are detailed in separate specifications ([FHIR R5](http://hl7.org/fhir/extensions/extensions-Patient.html), [V2.9.1](https://hl7.org/documentcenter/private/standards/V291_R1_202xmmm.zip), [Representing Sex and Gender in CDA](http://www.hl7.org/permalink/?GenderHarmonyCDAIG), this implementation 
guide provides specific additional guidance and cross-paradigm use cases. 

In this document, and elsewhere, the phrase “sex or gender” is used to characterize data in which the contextual meaning of the the datum is unclear and its use is an acknowledgement that human discourse regarding this information is often equally unclear. Use of this phrase is not intended to mean a unification of information that is more clearly either Sex Parameter for Clinical Use (SPCU) or gender identity.

### Model Overview

The conceptual model outlines the data elements, element attributes,
terminology bindings and relationships that clarify the meaning and
context of the information presented to guide and inform changes within
operational standards. The Model has five (5) major elements independent
of other components that may also be part of the information model for a
Person: Gender Identity (GI), Sex Parameter for Clinical Use (SPCU), Recorded Sex
or Gender (RSG), Name to Use (NtU), and Pronouns.

With the exception of one addition (Recorded Sex or Gender attribute =
type with datatype = code or constrained text) and one deletion (International Equivalent Recorded Sex or Gender), the model included in
this implementation guide is exactly as it is in the published Gender Harmony
informative specification. The addition was made to clarify and cover
the original intent of Record Sex or Gender, including the ability to
specify the type or category of sex or gender that is recorded (e.g.,
Sex Assigned At Birth). The deletion was made in response to ballot feedback that the RSG value element is a CodeableConcept which supports "translation" of local code values to other (international) code systems. 

Each of the following sections is structured to align with the UML Model
in Figure 1 and provides a definition, description, usage notes (if
applicable), cardinality, and attributes (with recommended terminology
if applicable) for each model element.


<figure>
{%include 2023genderharmony.svg%}
<figcaption><b>Figure 1: Logical Model for Gender Identity and Sex</b></figcaption>
</figure>
<br clear="all" />


The gender harmony model sub-elements described below are sex or
gender information that may be context-dependent; in essence a sex
and/or gender context type. Some of these types are multi-valued based
in part on the need for independent, occasionally co-occurring, values
that are specific to particular contexts of use within that type. The
sensitivity of these situations heightens the importance of representing
this data in a way that supports masking and access restrictions. The
Sex Parameter for Clinical Use (SPCU) can also be affected by independent
co-occurring contexts of use. Depending upon the procedure ordered, drug
prescribed, or nature of a clinical report different SPCUs might be
chosen. This can be reflected in the mapping chosen for a patient for
specific clinical reasons. The medical record in an EHR system might
have one set SPCU, and different specific selected SPCUs chosen for
mapping to NCPDP for a drug prescription, to FHIR for an order, to HL7
v2.x for another order, and to DICOM for an imaging request. This will
be especially common during the transition period when some systems have
been upgraded and others have not.

The rules for these context dependent mappings are not defined in this
abstract information model. They depend upon the concrete capabilities
of the target system, and upon the specific clinical context at the
time. It will be normal to find that when there are many objects related
to a single patient (orders, reports, observations, etc.) that there are
different SPCU due to differences in the context of use. Information
about the context and reason for selection may be incorporated into the
link to observations or reports that are part of the SPCU, or in the
comment associated with Gender Identity.

### Updates to the model compared to original specification
With the exception of the following noted changes, the model included in this implementation guide matches the model in the published Gender Harmony informative specification.
#### Recorded Sex or Gender
- Addition of Recorded Sex or Gender attribute = type with datatype = code or constrained text
   -  This addition was made to align with the original context of the data exchanged as an RSG so that users may specify the type or category of sex or gender that is recorded (e.g., "Sex").
-  Removed the InternationalEquivalentRecordedSexOrGender element
   -  Reviewers agreed that explicit inclusion of the translation of the value to a code from International Civil Aviation Organization (ICAO) code system was not useful. Implementers that want to send this may do so as a translation of the primary value.


#### Pronouns
- Update of Pronoun binding strength to Example.
   -  The binding strength to the Pronoun value set was originally extensible. Reviewers agreed that this needed to be loosened to example across products to allow for greater flexibility in establishing a base set of jurisdiction appropriate pronouns. 

### Person

**Definition:** This is an abstract representing a person.

**Usage Note:** This class may be mapped onto a concrete class when 
implemented using a model with concrete classes representing a person 
where additional attributes can be added or existing attributes can be 
enhanced. In FHIR currently this would be the following resources: Person, 
Patient, Practitioner, and RelatedPerson

### Gender Identity (GI)

Gender Identity describes the identity of the person. This
is important in many social and cultural contexts. It might be missing,
as for an infant, or multi-valued in some cultures and specific
situations. The meaning, criteria, and implications of specific gender
identities is defined by the local culture and society. The terms used
to capture GI are expected to reflect the variations found in different
cultures and locations, so only a minimum value set is defined in the
logical model. Local terminology is expected to extend this value set.

**Source:** Person, self-reported only

**Definition:** An individual's personal sense of being a man, woman,
boy, girl, nonbinary, or something else. This datum represents an
individual's identity, ascertained by asking them what that identity is.

**Usage Note:** If the Person (such as a fetus, infant, or uncommunicative new patient) is unable to express a personal sense of being a man, woman, boy, girl or any point on the gender spectrum, gender identity may be recorded as Unknown. Unknown can be used in cases where parents do not want to specify a value but one must be recorded. Gender identity can be congruent or incongruent with one’s SPCU or RSG. Persons may identify using different terms at different times for various reasons, or use multiple identities simultaneously, depending on culture.

Given that the gender identity element supports representing multiple gender identities (cardinality is 0..n), individuals who identify as having both Male and Female gender identities (or any other combination) at the same time, each gender identity can be modeled with the same validity period. Alternatively, if implementers and/or systems prefer to use a single code, the gender identity value set is expected to be used as a minimum value set that can be extended to meet jurisdictional requirements. One possible concept that could be considered is bigender.

**Cardinality:** 0..n

#### Attributes: 

##### Gender Identity

-   Definition:  An individual's personal sense of being a man, woman,
boy, girl, nonbinary, or something else. This datum represents an
individual's identity, ascertained by asking them what that identity is.

-   Cardinality 1..1

-   Type: Code or constrained short text

-   Proposed Terminology:

    -   [minValueSet](http://hl7.org/fhir/StructureDefinition/elementdefinition-minValueSet): [Gender Identity](http://terminology.hl7.org/ValueSet/gender-identity) valueSet

    -   [binding Strength](http://hl7.org/fhir/R5/terminologies.html#strength): [extensible](http://hl7.org/fhir/R5/terminologies.html#extensible)

##### Validity Period 

-   Definition: The time frame during which this Gender Identity applies
to the person. May be just an initial dateTime.

-   Usage note: Validity period may be overlapping in the case of
multiple gender identities (such as for bigender persons, some
gender-fluid persons, and binary Two-Spirit persons who also identify as
both male and female).

-   Cardinality: 0..1

-   Type: duration or datetime

##### Comment 

-   Definition: Text to further explain the use of the specified gender
identity or identities.

-   Usage note: Content included may be related to social and/or
cultural context to be considered when using the Gender Identity,
particularly with overlapping active values.

-   Cardinality: 0..1

-   Type: long text

### Sex Parameter for Clinical Use (SPCU)

Sex Parameter for Clinical Use is provided for use in orders, observations, 
and other clinical uses. SPCU can be highly contextual and allows specific
considerations to be provided for potential automated uses and records.
Examples include:

-   A person with polycystic ovary syndrome can be identified in a blood
    work order so that their unexpected hormone levels can be properly
    reported and not rejected as invalid results.

-   A female to male transgender patient early in transition undergoing imaging 
wherein the device requires selection of either M or F to complete the set up 
would benefit from an imaging context-specific SPCU noting the patient needs to 
have the setup for “Female-typical”

There are many other situations involving tumors, resections, congenital
conditions (i.e., ovotestes), and transgender patients where SPCU can be
used to provide information that is needed to perform a procedure
properly. Many procedures need at least a "male" or "female"
specification (e.g., for radiation shielding). 

SPCU provides a general extendable structure. During the transition from 
old systems to new systems, and as medical technology and science evolve, 
the rules for SPCU selection and referenced clinical observations will 
change. As technology changes these business rules may change, and the 
ordering systems are expected to accommodate changes to the order filling 
systems. The gender harmony model enables adaptation of old systems and 
new technologies.

The SPCU, when used for a specific observation, describes a context that 
clarifies the settings or reference ranges for the observation. For example, 
the computation of glomerular filtration rate (GFR) based on blood chemistry 
may use formulas that are different for “male” and “female”. The SPCU for 
the GFR report can indicate which formula should be used in the computation 
of that result. In cases where there is a patient level SPCU, the patient 
level value can be used as a default (any specific use) value unless a 
specific SPCU for that observation has been specified, in which case, the 
specified SPCU should apply. The gender harmony model does not cover the 
description of the use of SPCU in type of observation, but the approach for 
each is the same.

**Definition**: A Sex Parameter for Clinical Use is a parameter that 
provides guidance on how a recipient should apply settings or reference 
ranges that are derived from observable information such as an organ 
inventory, recent hormone lab tests, genetic testing, menstrual status, 
obstetric history, etc. This property is intended for use in clinical 
decision making, and indicates that treatment or diagnostic tests should 
consider best practices associated with the relevant reference population.

**Usage Note(s)**: A sex category that supports context specificity,
derived from observable information, preferably directly linked to the
information this element summarizes (such as a comment or a linked data
observation) in order to clarify the context and resulting value. This
element is intended to characterize observations that align with or vary
from female or male when the observation(s) are intended for use in a
clinical activity. In some systems the SPCU value may be automatically
determined based on the medical record so that they match the recipient
system's needs.

There may be restrictions on specific protocols or for specific targets.
The value multiplicity for a specific protocol or target may be 1..1 or
0..1. The GH model does not specify how such restrictions should be
implemented. They should reflect the purpose of the communication and
the capabilities of the systems involved. This may require individual
site specific business rules to map a multi-valued SPCU into a single
value that is appropriate for this context.

The model supports multiple instances of SPCU to allow, when necessary, 
more than one concurrent SPCU for a patient. For example, there could be 
multiple procedure results, each identifying a context specific SPCU 
determination used to set the normal range used. For example an SPCU value 
and linked comment or specific observation could be summarized as “male, 
based on hormonal measurement.”

**Cardinality**: 0..n, Multiple instances of an SPCU can exist and each 
instance will have the attributes listed below.

#### Attributes: 

##### SPCU Category 

-   Definition: A parameter that provides guidance on how a recipient 
should apply settings or reference ranges that are derived from observable 
information such as an organ inventory, recent hormone lab tests, genetic 
testing, menstrual status, obstetric history, etc.

-   Cardinality: 1..1

-   Type: Code or constrained short text

-   Proposed Terminology:

    -   ValueSet: [SexForClinicalUseCategory](http://terminology.hl7.org/ValueSet/sex-parameter-for-clinical-use) valueSet

    -   [binding Strength](http://hl7.org/fhir/R5/terminologies.html#strength): [required](http://hl7.org/fhir/R5/terminologies.html#required)

##### Validity Period

-   Definition: Time frame during which this summary value applies to
the patient. May be just an initial dateTime.

-   Usage Note: Validity period may overlap among different SPCU values
based on procedure or process used to determine the value

-   Cardinality: 0..1

-   Type: duration

##### Comment

-   Definition: Text to further explain the context for this specific
SPCU categorization. 
-   Usage note: Content included may be related to
social and/or cultural context to be considered or additional
information related to the linked observations, particularly with
overlapping active values

-   Cardinality: 0..1

-   Type: long text

##### Linked Clinical Observation

-   Definition: Link to, or identifier of, the observation(s) or report(s) that
are used to determine the sex category value.

-   Usage Note: The specific implementation of these links will vary
based on the standard used. This GH model does not specify the encoding
mechanism for a link. It could be a DOI, a URL, a DICOM SCOORD-3D, etc.
The specific standards and implementations will specify this. The linked
information should clearly align with the chosen SPCU. For example, a
patient with an initial diagnosis of an intersex condition could have
supporting clinical observations specific to the diagnosis. Additional
information may be provided in the Comment attribute.

-   Cardinality: 0..n

-   Type: string

### Recorded Sex or Gender (RSG)

Recorded Sex or Gender information may originate from a physical or electronic document that was provided to a medical provider. This information may also originate from fields in medical systems that were initially populated using those documents, or via patient attestations.  The rules for collection of these documents and fields have varied significantly over time and place therefore  the relationship to current Gender Identity or Sex Parameters for Clinical Use may be unclear. 

The RSG model includes source information so that the definition of “X” in a driver’s license can be found if necessary and the jurisdiction can be recorded.


**Definition:**  Recorded Sex or Gender (RSG) information includes the various sex and gender concepts that are often used in existing systems but are known to NOT represent a Gender Identity, Sex Parameter for Clinical Use, or attributes related to sexuality, such as sexual orientation, sexual activity, or sexual attraction.

**Usage Note:** If a medical system needs to exchange a single internal field labeled “sex” which, over time, has been used to capture both sex and gender, Recorded Sex or Gender may be an appropriate way to exchange such data. 

It is understood that administrative gender, administrative sex, and sex assigned at birth are exchanged today, and when exchanged in this way the data should not be considered a representation of Gender Identity (GI) or Sex Parameter for Clinical Use (SPCU). It is expected that these concepts may continue to be exchanged using existing established methods without using RSG. But, when SAAB *is exchanged as an RSG entry* the "type” should be specified as “sex assigned at birth” or another regionally specific short text string. As a result of feedback from the Gender Harmony Project and in-line with the gender harmony model, the US Office of the National Coordinator (ONC) recognized in its Standards Bulletin (SB22-2), regarding the development and finalization of United States Core Data for Interoperability (USCDI) Version 3, that “the data element Sex (Assigned at Birth) is used to represent different concepts not necessarily associated with what is assigned at the time of birth, such as clinically relevant sex for labs or diagnostic imaging, as well as administrative sex as recorded on birth certificates and health forms.” As a result, ONC changed the name of the data element to “Sex” acknowledging the previous limitation to birth information documentation.

**Cardinality:** 0..n

**Guidance:**
When evaluating when and how to exchange sex or gender concepts, consider whether Gender Identity or Sex Parameters for Clinical Use may be better for the relevant use case.  If those concepts are not appropriate or available, then the following approach for exchanging Recorded Sex or Gender may be used:

1. Determine which sex or gender concept is relevant for the jurisdiction and use case.  For example, you might identify concepts such as:
   * Sex Assigned at Birth
      * For clinical purposes, consider whether Sex Parameters for Clinical Use may more accurately represent the patient’s relevant clinical status.
      * Sex Assigned at Birth may not reflect current clinical attributes of adults.
      * Understand that the Sex Assigned at Birth value in medical systems may not be the value recorded on the birth certificate at the time of birth due to operational and training issues around its collection.

   * Administrative Sex/Gender
      * For the purpose of communicating with a patient, consider whether Gender Identity may be more appropriate.
   * Legal Sex/Gender
   * Billing Sex/Gender
   * Etc.
2. Determine the best way to exchange this information between systems.  This could involve:
   * Using existing fields (and their associated terminology) such as:
      * Patient.gender in FHIR
      * PID-8, GT1-9, NK1-15 in HL7v2
      * Birth Sex Observation template or Patient.administrativeGenderCode in CDA
   * Creating jurisdiction or use case specific structures that are directly tied to the specific concept being exchanged, such as:
      * New jurisdictional or use case specific extensions for FHIR
      * [us-core-birthsex](http://hl7.org/fhir/us/core/StructureDefinition-us-core-birthsex.html)
	   * [us-core-sex](http://hl7.org/fhir/us/core/StructureDefinition-us-core-sex.html)
      * [ukcore-birthsex](https://simplifier.net/hl7fhirukcorer4/extension-ukcore-birthsex)
      * New template for CDA
   * Using a generic structure
      * The individual-recordedSexOrGender FHIR extension if available for the context in question
      * A FHIR Observation resource
      * OBX or GSR segments in HL7v2
      * Observation template in CDA


The value sets used to exchange Recorded Sex or Gender values are expected to be defined by the owner of the specific concept being exchanged.  For example, if you are exchanging the sex on the driver's license in a specific region, that region's driver registration authority would define the value set, and those values would be used in the exchange.  As such, creating new value sets to represent Recorded Sex or Gender values is not necessary and should be avoided.

#### Attributes: 

##### Source Recorded Sex or Gender 

-   Definition: The actual value found on the document. This may be in
any character set. For example, a Russian identity card might have the
value 'ж' for sex.

-   Cardinality: 1..1

-   Type: Code or constrained short text

Note that based upon ballot feedback, the proposed InternationalEquivalentRecordedSexOrGender element with values based upon the International Civil Aviation Organization (ICAO) code system is no longer included. Implementers may provide an ICAO translation to the value provided.


##### Type

-   Definition: The type or category of sex or gender identity that is recorded.

-   Cardinality: 0..1

-   Type: code or constrained text

##### Record Description

-   Definition: A short phrase that describes the document or record
that includes the sex or gender identity value. E.g., national ID card, birth
certificate, passport.

-   Cardinality: 0..1

-   Type: string

##### Acquisition Date

-   Definition: The date that the document was scanned, processed, etc.
to extract the sex or gender identity information.

-   Cardinality: 0..1

-   Type: datetime

##### Validity Period

-   Definition: The time frame during which the document is valid. May be just an
initial dateTime.

-   Cardinality: 0..1

-   Type: duration

##### Issuer

-   Definition: Jurisdiction or organization that issued the document.

-   Cardinality: 0..1

-   Type: string

##### Source Field Name

-   Definition: Name of the source field in the document for this Recorded 
Sex or Gender instance.

-   Usage Note: This may be in any character set. For example, on a Russian
identity card it could be 'Пол'.

-   Cardinality: 0..1

-   Type: string

##### Source Field Description

-   Definition: A description of the source field in the document for this 
Recorded Sex or Gender instance.

-   Usage Note: Further description of the source field to clarify
intent of meaning. This may be a link or an external reference. For
example, there is an international standard for the fields on an
international travel passport.

-   Cardinality: 0..1

-   Type: string

### Name to Use (NtU)

The Name to Use enables care providers to use the name that is chosen by
the person. This element may match but is distinct from a person's legal
name and is the appropriate name to be used in person-centered
healthcare conversations. Some cultures have very long names, and expect
that for all but mandatory legal situations, the person will use a more
manageable name. Jurisdictions have different rules and processes for
name changes, so there is often a mismatch that can be prolonged in
difficult situations.

**Definition:** Text attribute that provides the name that should be
used when addressing or referencing the patient.

**Usage Note:** This information is usually provided by the patient.
Depending on the standard applicable to an implementation, this might be
encoded within a Person/Patient Name field with an appropriate name type
qualifier but is independent of any other name type or name component.
This may be a nickname or formal name. Multiple cardinalities are
required to support changes in desired name over time, such as when a
patient desires a change in name to align with expressed gender identity. This
means a validity period and a comment attribute to allow text that can
be used to capture context for use of the name.

**Cardinality:** 0..n

#### Attributes: 

##### Name 

-   Definition: Name to Use when addressing or referencing the patient.

-   Cardinality: 1..1

-   Type: string

##### Validity Period

- Definition: The timeframe during which the Name is to be used. May
just include a start date.

-   Cardinality: 0..1

-   Type: duration

##### Comment

--  Definition: Text to further explain use of the Name. This may be
related to social and/or cultural context.

-   Cardinality: 0..1

-   Type: long text

### Pronouns

**Definition:** Pronoun(s) specified by the patient to use when
referring to the patient in speech, in clinical notes, and in written
instructions to caregivers.

**Usage Note:** Personal pronouns are words used instead of a noun or a noun phrase used to refer to people. Avoiding incorrect pronoun use and patient misgendering is crucial in providing care to gender-diverse populations. It is important to reliably exchange personal pronouns that the individual has specifically reported they want used. The information could be considered a primary (first class) element associated with the demographic information for
the patient. However, it may require representation as an observation about the patient. Local policy will determine how pronouns are chosen for infants and other similar situations. Policy and local custom will determine what to use when this attribute is not present, or when
multiple are present.

Different pronouns may be used in one care setting than another care
setting. The pronouns used in the work environment may be different than
those in the care setting. 

**Cardinality:** 0..n

#### Attributes: 

##### Pronoun 

-   Definition: The noun or a noun phrase used for the patient.

-   Cardinality: 1..1

-   Type: Code or constrained short text

-   Proposed Terminology:

    -   ValueSet: [Pronouns](http://terminology.hl7.org/ValueSet/pronouns) valueSet

    -   [binding Strength](http://hl7.org/fhir/R5/terminologies.html#strength): [example](http://hl7.org/fhir/R5/terminologies.html#example)

##### Validity Period

-   Definition: The timeframe during which the pronoun is to be used.
May just include a start date.

-   Cardinality: 0..1

-   Type: duration

##### Comment

-   Definition: Text to further explain use of the pronoun.

-   Usage Note: Multiple pronoun entries may exist and overlap as some
persons utilize multiple pronouns simultaneously or switch usage based
on context, familiarity, comfortability, and/or Gender Identity (for
instance, in the case of bigender or gender-fluid persons).

-   Cardinality: 0..1

-   Type: long text
