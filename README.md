# HR-Analytics-Atliq_masked
This is  one of a Codebasics Resume Project Report on HR Analytics for AtliQ Hardware

## Show my dashboard below on my Portfolio
https://www.novypro.com/project/hr-analytics-atliqmasked

Project Overview:

In this  project, So we have 3 month of data of the year 2022 that is  in the form of Excel sheets having attendance key and employee attendance.
So,  HR manager  wants some insights from this data, which is listed below:

HR manager requirements are as follows:
1. The reason behind the frequently WFH.
1. The working preference of people between WFH and WFO?
2. The percentage of Sick leave to monitor employee wellness?
3. How much percent of people are present on a given week or a month?
4. Which day in a week is when most of the people are present so that they can plan an event on that day?
5. The pattern of sick leave so if there is a situation of epidemic or flu, they can do proper precaution or special measure.

Key Insights:

1. Presence % by month is declining so, It may be due to the summer season.
2. WFH % of working people is increasing.
3. SL % is a little bit increasing.
4. Most of the employees prefer WFH on Friday.
5. Most of the employees are present on Monday.

   ![HR_analysis](https://github.com/pravalenka/HR-Analytics-Atliq_masked/assets/120097217/4dd994a2-40bf-4611-992b-351f678077f3)

## DAX function have used in this analysis-
   
1. SL Count = SWITCH(
    TRUE(),
    'Final Data'[Value]="SL",1,
  'Final Data'[Value]="HSL", 0.5,
    0)

2. WeekNo = "W " & WEEKNUM('Final Data'[Date])

3. WFH Count = SWITCH(
    TRUE(),
    'Final Data'[Value]="WFH",1,
  'Final Data'[Value]="HWFH", 0.5,
    0)

4. Attendace % = 
DIVIDE([Present Days],[Office Working days],0)


5. HFWH Count = CALCULATE([Count],'Final Data'[Value]="HWFH")

6. Office Working days = 
Var totaldays = [Count]

VAR nonworkdays = CALCULATE([Count],'Final Data'[Value] in {"HO", "WO"})

RETURN
totaldays-nonworkdays

7. Present Days = CALCULATE([Count],'Final Data'[Value] in {"P", "WFH"}) 

8. SL % = DIVIDE('Measures (2)'[SL Count], [Office Working days])

9. SL Count = SUM('Final Data'[SL Count])

10. WFH % = DIVIDE([WFH Count],'Measures (2)'[Present Days],0)

11. WFH Count = SUM('Final Data'[WFH Count])

12. day of week = FORMAT( 'Final Data'[Date], "ddd")
