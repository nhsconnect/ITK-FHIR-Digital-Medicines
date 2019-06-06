---
title: Allergies and Adverse Reactions Section
keywords:  messaging, sections
tags: [fhir,messaging,section]
sidebar: foundations_sidebar
permalink: explore_allergies_and_adverse_reactions.html
summary: "Gives information about the Allergies and Adverse reactions section"
---

{% include custom/section.warnbanner.html %}

## Allergies and Adverse Reactions Section Content ##
The Allergies and adverse reactions section carries information about the patient's allergies and adverse reactions. PRSB Elements should be formatted as subheadings in any HTML sent.
This table should be used in conjunction with the section on [constructing clinical coded structures](build_allergy_lists.html) for further information on constructing and coding allergy lists. 

<table style="width:100%;max-width: 100%;">
	<thead>
		<tr>
			<th width="15%">Section</th>
			<th width="35%">Description</th>
			<th width="5%">Card.</th>
			<th width="5%">MRO*</th>
			<th width="40%">FHIR Target and Guidance</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Allergies and adverse reactions</td>
			<td>The details of any known allergies, intolerances or adverse reactions.</td>
			<td>1 only</td>
			<td>O</td>
			<td>Carried in the CodeableConcept of <b>Composition.section.code</b> FHIR element.</td>
		</tr>
		<tr>
			<th>PRSB Element</th>
			<th>Description</th>
			<th>Card.</th>
			<th>MRO*</th>
			<th>FHIR Target and Guidance</th>		
		</tr>
		<tr>
			<td>Causative agent</td>
			<td>The agent such as food, drug or substances that has caused or may cause an allergy, intolerance or adverse reaction in this patient.</td>
			<td>1 only</td>
			<td>M</td>
			<td>Text and a SNOMED CT concept carried in the CodeableConcept of <b>AllergyIntolerance.code</b> FHIR element. For further information on coding causative agent see <a href="build_allergy_lists.html#causative-agents">Constructing Allergy Lists (Causative agents).</a></td>
		</tr>
		<tr>
			<th colspan="5">Reaction details cluster</th>
		</tr>
		<tr>
			<td>Description of reaction</td>
			<td>A description of the manifestation of the allergic or adverse reaction experienced by the patient. For example, skin rash.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Text and if coding is available carried in the CodeableConcept of the <b>AllergyIntolerance.reaction.manifestation</b> FHIR element. If no coding is available use the <b>AllergyIntolerance.reaction.description</b> FHIR element. For further information on reaction details see <a href="build_allergy_lists.html#reaction-details">Constructing Allergy Lists (Description of reaction).</a></td>
		</tr>
		<tr>
			<td>Severity</td>
			<td>A description of the severity of the reaction</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>mild | moderate | severe. Text and if coding is available carried in the CodeableConcept of the <b>AllergyIntolerance.reaction.severity</b> FHIR element. For further information on severity see <a href="build_allergy_lists.html#severity">Constructing Allergy Lists (Severity)</a>.</td>
		</tr>
		<tr>
			<td>Certainty</td>
			<td>A description of the certainty that the stated causative agent caused the allergic or adverse reaction.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>unconfirmed | confirmed. Text and if coding is used available carried in the Code of <b>AllergyIntolerance.verificationStatus</b> FHIR element. For further information on certainty see <a href="build_allergy_lists.html#certainty">Constructing Allergy Lists (Certainty)</a>.</td>
		</tr>
		<tr>
			<td>Comment</td>
			<td>Any additional comment or clarification about the adverse reaction.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Free text</td>
		</tr>
		<tr>
			<td>Date recorded</td>
			<td>The date that the reaction was clinically recorded/asserted. This will often equate to the date of onset of the reaction, but this may not be wholly clear from source data.</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>dateTime. The date that the reaction was clinically recorded/asserted. Text and carried in <b>AllergyIntolerance.assertedDate</b> FHIR element.</td>
		</tr>
		<tr>
		<th colspan="5">End of Reaction details cluster</th>
		</tr>
		<tr>
			<td>Type of reaction</td>
			<td>The type of reaction experienced by the patient (allergic, adverse, intolerance)</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>allergy | intolerance. Text and if coding is available carried in Code of <b>AllergyIntolerance.type</b> FHIR element. For further information on certainty see <a href="build_allergy_lists.html#type-of-reaction">Constructing Allergy Lists (Type of reaction)</a></td>
		</tr>
		<tr>
			<td>Evidence</td>
			<td>Results of investigations that confirmed the certainty of the diagnosis. Examples might include results of skin prick allergy tests</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Reference (DiagnosticReport). Free text. Note: structured FHIR Diagnostic Reports are not currently supported in Digital Medicines. An attachment such as a pdf of a laboratory report may be included with a link as evidence. See section on <a href="build_attachments.html">Use of attachments</a></td>
		</tr>
		<tr>
			<td>Probability of recurrence</td>
			<td>Probability of the reaction (allergic, adverse, intolerant) occurring</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>Free text</td>
		</tr>
		<tr>
			<td>Date first experienced</td>
			<td>When the reaction was first experienced. May be a date or partial date (e.g. year) or text (e.g. during childhood)</td>
			<td>0 to 1</td>
			<td>R</td>
			<td>dateTime | Age | Period | Range | String. Free text and <b>AllergyIntolerance.onset[x]</b> FHIR element. For further information see <a href="build_allergy_lists.html#date-first-experienced">Constructing Allergy Lists (Date first experienced)</a></td>
		</tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
	</tbody>
</table>



##  Example Allergies and Adverse Reactions Section ##

```
<xml>
<!--Allergies and adverse reactions-->
	<section>
		<title value="Allergies and adverse reactions"/>
	<code>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="886921000000105"/>
			<display value="Allergies and adverse reactions"/>
		</coding>
	</code>
	<text>
	<status value="additional"/>
	<div xmlns="http://www.w3.org/1999/xhtml">
		<table width="100%">
			<tbody>
				<tr>
					<th>Causative agent</th>
					<td>No known allergy</td>
				</tr>
			</tbody>
		</table>
	</div>
	</text>
	<!--Reference to Allergies List as the source of information for this section-->
	<entry>
		<reference value="urn:uuid:66204550-8e57-11e8-b568-0800200c9a66"/>
	</entry>
	</section>
</xml>
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- List
- AllergyIntolerance
 
See constructing clinical coded structures - [Allergy Lists](build_allergy_lists.html)











