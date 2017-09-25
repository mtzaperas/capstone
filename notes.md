## Business goal
Do police know what busy intersections to patrol? Do paramedics know problem intersections? What if they knew areas they likely were needed

Sources:
https://www.quora.com/Are-police-officers-assigned-areas-to-patrol-or-do-they-just-roam-around-freely


## Specific problem statement
There are a lot of different slices I could investigate. I could look at accidents involving injuries/death, involving alochol or drugs, involving weather, who reported incident (cop saw it or civilian called it in)

DUI: happens at night, as expected
DUI: varies from month to month, year to year, not entirely consistent
DUI weather: not an impact
Nondui: happens in traffic hours, as expected
Nondui: happens consistently from month to month
Nondui weather: mostly clear, most weather incidents are cloudy and then 2nd rainy
Who reported it?

The avenue I decided to go down is, given information about the driver (from austin, his/her car make/model) and time of year/month/day, how likely are they to be injured in each given zip code. Could overlay that on google map routes. Could start to include information like how old the driver is, has he/she been drinking/smoking, the contributing factors (animals on road vs road rage vs drinking)

It would be nice to actually predict chances of crash rather than chances of severe injuries. Austin has 3000 data points across the past 17 years on spotty locations. I could use that limited information and assume linear growth.
## EDA
To get the data, go to https://cris.dot.state.tx.us, choose \*Texas Department of Transportation and create account/login. I made requests of type public, in .csv format, for Travis County.
I've begun exploring the Travis County traffic data for 2017. It is separated into different csv files, so the first step is joining all of them together. Some csv files have duplicated column names with different values. I need to see if the data dictionary provided indicates this is intended or not.

For weather data, I'm using NOAA (govt data). I also have weather underground information I could web scrape.

Austin opendata effort has published Austin Police Sectors and Districts:
https://data.austintexas.gov/Government/Austin-Police-Sectors-and-Districts/bh6h-vpxb
APD also defines what it considers rush hour and says it has tow trucks on standby to clear busy roads:
http://www.austintexas.gov/page/highway-enforcement-programs
Austin EMS publishes metrics on how its doing, and all metrics point to doing fine. No map tho:
http://www.austintexas.gov/department/performance-metrics



**Columns to split/not split on**
Charges column was changed from categorical to free entry before 2010 (according to data dict). I'd have to manually bucket the charges, which can include abbr and multiple charges per unique charge


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
- Unit_Nbr: *number entered on crash report for each car/vehicle/bike/person involved in the crash*
- Person, PrimaryPerson, Charges
-  Prsn_Nbr: *The person who was charged*
  - Person, PrimaryPerson, Charges

**Merging tables**
- Concat the person, primaryperson tables together in pandas since almost all same columns and don't have overlap in ppl discussed in each
- Problem with merging charges table - columns Unit_Nbr and Prsn_Nbr identical to person, primaryperson tables. Solved by merging charges table with on key = [Charge_ID, Unit_Nbr, Prsn_Nbr]
- Multiple persons (Prsn_Nbr) per crash, multiple charges per person
- Some columns may be deprecated (charge cat ID stopped being used in 2010 per data dictionary)
- Decided to use crash_ID as index for joining unit to crash, then to reset index to crash_ID and unit (multiindex), then to add people information. Could add further tables with new multiindex that adds prsn_nbr
