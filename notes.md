
## EDA
I've begun exploring the Travis County traffic data for 2017. It is separated into different csv files, so the first step is joining all of them together. Some csv files have duplicated column names with different values. I need to see if the data dictionary provided indicates this is intended or not.

**Columns not in data dictionary**
*From Unit. These are populated when other columns in unit are not. Seems weird*
- Trlr_GVWR
-	Trlr_RGVW
-	Trlr_Type_ID
-	Trlr_Disabling_Dmag_ID
*From Crash. Not text, number. No dictionary to decode it either*
- Investigator_Narrative

**Count type Column Duplication**
*Duplicated across Crash, Person, Primary Person, Unit tables*
- Death_Cnt
- Incap_Injry_Cnt
- Nonincap_Injry_Cnt
- Non_Injry_Cnt
- Poss_Injry_Cnt
- Unkn_Injry_Cnt
- Tot_Injry_Cnt

**Person/Primary Person Duplication**

 *only difference btwn Person/Primary person are the driver information columns*
- Prsn_Alc_Rslt_ID: *If person tested positive/negative for alcohol*
- Prsn_Drg_Rslt_ID: *If person tested positive/negative for drugs*
- Prsn_Ethnicity_ID: *Ethnicity of person involved in the crash*
- Prsn_Injry_Sev_ID: *Severity of injury to the occupant*
- Prsn_Sol_Fl: *Solicitation*
- Prsn_Occpnt_Pos_ID: *The physical location of an occupant in, on, or outside of the motor vehicle prior to the First Harmful Event or loss of control*
- 'Prsn_Bac_Test_Rslt',
- 'Prsn_Type_ID',
- 'Prsn_Death_Time',
- 'Prsn_Ejct_ID',
- 'Prsn_Gndr_ID',
- 'Prsn_Airbag_ID',
- 'Prsn_Helmet_ID',
- 'Prsn_Alc_Spec_Type_ID',
- 'Prsn_Drg_Spec_Type_ID',
- 'Prsn_Age',
- 'Prsn_Rest_ID',

**Other Duplications**
- Crash_ID: *acts as primary key for each table*
- Unit_Nbr: *Unit number entered on crash report for a unit involved in the crash*
- Person, PrimaryPerson, Charges
-  Prsn_Nbr: *The person who was charged*
  - Person, PrimaryPerson, Charges

**Merging tables**
- Grouped person, primaryperson tables together to prevent duplicating identical columns
- Problem with merging charges table - columns Unit_Nbr and Prsn_Nbr identical to person, primaryperson tables. Solved by merging charges table with on key = [Charge_ID, Unit_Nbr, Prsn_Nbr]
- Multiple persons (Prsn_Nbr) per crash, multiple charges per person
- Some columns may be deprecated (charge cat ID stopped being used in 2010 per data dictionary)
