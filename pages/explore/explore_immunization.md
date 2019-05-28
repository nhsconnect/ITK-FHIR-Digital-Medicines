---
title: Immunisations Section
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_immunization.html
summary: "Gives information about the Immunisations section"
---

{% include custom/section.warnbanner.html %}

## Immunisations Section Content ##
The Immunisations section carries information about the immunisation administered. PRSB Elements should be formatted as subheadings in any HTML sent.


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
   <td>Immunisations section</td>
   <td>This acts as a container that holds all of the elements for each instance of an vaccination entry.</td>
   <td>1 only</td>
   <td>M</td>
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
   <td>Vaccine product</td>
   <td>Vaccine product administered.</td>
   <td>1 only</td>
   <td>M</td>
   <td>Choice of<br/>
 • Text<br/>
 • Coded text - constraint: MedicationName. Any AMP/VMP/VTM/AMPP/VMPP subsets from the dm+d terminology. NHS dm+d AMP ::352201000001139 NHS dm+d AMPP ::352401000001135 NHS dm+d VMP ::352701000001133 NHS dm+d VMPP ::352301000001131 NHS dm+d VTM ::352601000001138. Constraint binding: [dm+d]subset=NHS_dm+d<br/>
(In the future needs to be GS1 code mapped to dm+d)</td>
  </tr>
  <tr>
   <td>Vaccine procedure</td>
   <td>The vaccination that was given e.g. seasonal influenza vaccination.</td>
   <td>1 only</td>
   <td>M</td>
   <td>For seasonal flu vaccinations the following coded text should be used:<br/>
<br/>
955691000000108 | Seasonal influenza vaccination given by pharmacist (situation) |<br/>
<br/>
Note that 849211000000109 | seasonal influenza vaccination given by pharmacist (finding) | in the NHSE service specification was made inactive in April 2015 and was replaced by the concept above
<br/><br/>
For general vaccinations the following coded text should be used: <br/>
<<33879002 |Active immunisation|<br/>
<<304250009 |Immunisation status|<br/>
<<713404003 |Vaccination given|<br/>
<br/><br/>
In addition there are some scattered concepts below in the situations hieararchy.<br/>
<<955641000000103 |Influenza vaccination given by other healthcare provider|<br/>
955701000000108 |Seasonal influenza vaccination given while hospital inpatient|<br/>
<<957581000000102 |Meningitis B vaccination given by other healthcare provider|<br/>
957751000000103 |Meningitis ACW & Y vaccination given by other healthcare provider|<br/>
<<1066171000000108 |Seasonal influenza vaccination given by midwife|<br/>
140611000119104 |Human papilloma virus type 16 and 18 vaccination given|
</td>
  </tr>
  <tr>
   <td>Manufacturer</td>
   <td>Name of vaccine manufacturer</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>Derived from GS1 code/free text</td>
  </tr>
 <tr>
   <td>Serialisation code</td>
   <td>A code that separately identifies two identical vaccines (i.e. same product, same batch).</td>
   <td>0 to 1</td>
   <td>O</td>
   <td>Derived from FMD code or free text.</td>
  </tr>
 <tr>
   <td>Site</td>
   <td>Body site vaccine was administered into.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>Choice of<br/>
 • Text<br/>
 • Coded text – constraint: SiteOfMedicationAdministration. Any valid site for the administration of a medication. Constraint binding: [SNOMED-CT]subset= SiteOfMedicationAdministration</td>
  </tr>
 <tr>
   <td>Route</td>
   <td>How vaccine entered the body.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>• Coded text – constraint: NHS e-prescribing route of administration subset ID: 413001000001136 Original Id : 30201000001137 This is an extract from the SUBSET -BiAnnual-Drug-15.0.1-20130401: SnomedCT_GB1000001_20130401/Subsets/EPrescribing/NHS e-Prescribing route of administration subset. Constraint binding: [SNOMED-CT]subset=NHS e-Prescribing route of administration subset.</td>
  </tr>
 <tr>
   <td>Indication</td>
   <td>The clinical indication or reason for administering the vaccine.</td>
   <td>0 to 1</td>
   <td>O</td>
   <td>This will be free text/proposal to use the list from below (as an example list)<br/>
Routine mass immunisation  171279008|Immunization due (finding)|<br/>
<br/>
Travel to endemic area  414448007|Identified as high risk for travel immunization (finding)|<br/>
Planned travel to high risk area 161096004|Going to travel abroad (finding)|<br/>
Recent travel to high risk area 506931000000109|Recent travel to disease affected area (finding)|<br/>
<br/>
Subpopulation at special or unusual risk  78648007|At risk for infection (finding)|<br/>
High risk due to occupation 14679004 Occupation (occupation)<br/>
High risk due to lifestyle 134436002|Lifestyle (finding)|<br/>
High risk due to existing medical condition 398192003|Co-morbid conditions (finding)|<br/>
<br/>
Control of known sporadic outbreak  443684005|Disease outbreak (event)|<br/>
<br/>
Patient request  183995001|Patient requested procedure (situation)|<br/>
<br/>
Post-exposure prophyaxis  444107005|Exposure to communicable disease (event)|<br/>
<br/>
Other  723620004|Requires vaccination (finding)
</td>
  </tr>
 <tr>
   <td>Dose amount</td>
   <td>Amount of vaccine administered.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>This will be free text. Coded units of measure (from DM+D)</td>
  </tr>
 <tr>
   <td>DateTime</td>
   <td>The date/time on which the vaccine was administered.</td>
   <td>0 to 1</td>
   <td>R</td>
   <td>The date/time as recorded by the pharmacy system. This will be carried in the FHIR element <b>Immunization.date</b>.</td>
  </tr>
		<tr>
		<td colspan="5"><b>* M=Mandatory R=Required O=Optional</b></td>
		</tr>
 </tbody>
</table>


## Example Immunisations Section ##

<script src="https://gist.github.com/IOPS-DEV/e3f8338cef252ede9812669198d2fa71.js"></script>

## Coded Resources ##

This text section should be linked to the following FHIR Resources to provide the textual information in a coded format.

- Immunization
 
