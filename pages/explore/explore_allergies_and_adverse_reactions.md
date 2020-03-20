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

| ALLERGIES   & ADVERSE REACTIONS |                                                                                                                                                                                                                               |             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                  |                                                                                                                                                                                                                      |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Data Item                       | Description                                                                                                                                                                                                                   | Cardinality | Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Mandatory/required/     optional | FHIR Target                                                                                                                                                                                                          |
| Causative agent                 | The   agent such as food, drug or substances that has caused or may cause an   allergy, intolerance or adverse reaction in this patient. Or “No known drug   allergies or adverse reactions” Or “Information not available”.  | 1   ONLY    | Choice   of       • Text      • Coded text – constraint: SNOMED   CT:       NHS dm+d TF,       NHS dm+d TFG,       NHS dm+d VMP,       NHS dm+d AMP,      NHS dm+d Ingredients,       NHS dm+d Combination drug VTMs,               Or alternatively one of the   following statements:      “No known drug allergies or adverse   reactions” Or “Information not available” (Comment coding for this should be   reviewed as the GP2GP causative agent work reaches completion) | Mandatory                        | AllergyIntolerance.code                                                                                                                                                                                              |
| Description of reaction         | A   description of the manifestation of the allergic or adverse reaction   experienced by the patient. For example, skin rash.                                                                                                | 0   TO 1    | Free   text                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                         | Text and if coding   is available carried in the CodeableConcept of the   AllergyIntolerance.reaction.manifestation FHIR element. If no coding   available use AllergyIntolerance.reaction.description FHIR element. |
| Type of reaction                | The   type of reaction experienced by the patient (allergic, adverse, intolerance).                                                                                                                                           | 0   TO 1    | allergy   - intolerance                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Required                         | AllergyIntolerance.type                                                                                                                                                                                              |
| Severity                        | A   description of the severity of the reaction.                                                                                                                                                                              | 0   TO 1    | mild   - moderate - severe                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Required                         | AllergyIntolerance.reaction.severity                                                                                                                                                                                 |
| Certainty                       | A   description of the certainty that the stated causative agent caused the   allergic or adverse reaction.                                                                                                                   | 0   TO 1    | unconfirmed   - confirmed                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Required                         | AllergyIntolerance.verificationStatus                                                                                                                                                                                |
| Evidence                        | Results   of investigations that confirmed the certainty of the diagnosis. Examples   might include results of skin prick allergy tests.                                                                                      | 0   TO 1    | Reference   (DiagnosticReport)                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Required                         | Composition.section.text   Note: structured FHIR Diagnostic Reports are not currently supported                                                                                                                      |
| Probability of recurrence       | Probability   of the reaction (allergic, adverse, intolerant) occurring.                                                                                                                                                      | 0   TO 1    | Free   text                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                         | Composition.section.text                                                                                                                                                                                             |
| Date first experienced          | When   the reaction was first experienced. May be a date or partial date (e.g. year)   or text (e.g. during childhood).                                                                                                       | 0   TO 1    | dateTime   - Age - Period - Range - String                                                                                                                                                                                                                                                                                                                                                                                                                                       | Required                         | AllergyIntolerance.onset[x]                                                                                                                                                                                          |
| Comment                         | Any   additional comment or clarification about the adverse reaction.                                                                                                                                                         | 0   TO 1    | Free   text                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Required                         | Composition.section.text                                                                                                                                                                                             |
| Date recorded                   | The   date that the reaction was clinically recorded/asserted. This will often   equate to the date of onset of the reaction but this may not be wholly clear   from source data.                                             | 0   TO 1    | dateTime                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Required                         | AllergyIntolerance.assertedDate                                                                                                                                                                                      |

##  Example Allergies and Adverse Reactions Section ##

{% include note.html content="These examples have not been clinially assured against Digital Medicines use cases.<br/>Examples are illustrative only." %}

```
<!--<xml>-->
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
										<td>NHS dm+d TF</td>
									</tr>
									<tr>
										<th>Description of reaction</th>
										<td>Signs of a skin rash</td>
									</tr>
									<tr>
										<th>Type of reaction</th>
										<td>allergy</td>
									</tr>
									<tr>
										<th>Severity</th>
										<td>mild</td>
									</tr>
									<tr>
										<th>Certainty</th>
										<td>unconfirmed</td>
									</tr>
									<tr>
										<th>Probability of recurrence</th>
										<td>Until the cause of the allergy is determined the chances of it coming back are high.</td>
									</tr>
									<tr>
										<th>Date first experienced</th>
										<td>9-May-2018 10:00</td>
									</tr>
									<tr>
										<th>Comment</th>
										<td>Suggest refer to a dermatologist</td>
									</tr>
									<tr>
										<th>Date recorded</th>
										<td>10-May-2018 10:00</td>
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
<!--</xml>-->
```

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- List
- AllergyIntolerance
 
See constructing clinical coded structures - [Allergy Lists](build_allergy_lists.html)