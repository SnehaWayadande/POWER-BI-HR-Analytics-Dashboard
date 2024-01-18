# POWER-BI-HR-Analytics-Dashboard

## **Introduction**
This project is aimed to developing a power Bi Dashboard for generating insights about Employees attendance data in the organization.
The dataset can be accessed from **DataSet** folder.

## **Installation / Usage**
- Install Power BI Desktop from official Power BI Desktop	
- Download data file from dataset folder.
- Open Dashboard report file(HR-Analytics-Dashboard.pbix) in Power Bi Desktop, to access the dashboard’s interactivity.

## **Dashboard Requirements**
- Display Employees monthly attendance reports.
- Insights of  Working preference of Employees Between work from home and work from office.
- Total Count of Sick leaves % , presence %, work from home % on weekly basis.

## **DAX Formulas Used in Measures**

#### Total Working Days of employees(Monthly) :
~~~
Total Working Days = 
Var totaldays = COUNT('Final Data'[Value])
Var nonworkdays = CALCULATE(COUNT('Final Data'[Value]),'Final Data'[Value] in {"WO", "HO"})
RETURN
totaldays-nonworkdays
~~~

#### Total Present Days of employees(Monthly) : 
~~~
Present Days =  VAR Presentdays = CALCULATE(COUNT('Final Data'[Value]),'Final Data'[Value]="P")
RETURN
Presentdays + [WFH Count]
~~~

#### Presence % Measures -
~~~
Presence % = DIVIDE([Present Days],'Measure Table'[Total Working Days],0)
~~~

#### Work From Home % Measures -
~~~
WFH Count = SUM('Final Data'[WFH Count])

WFH % = DIVIDE([WFH Count], [Present Days],0)
~~~


#### **Sick Leave % Measures -**
~~~
SL Count = SUM('Final Data'[SL Count])

SL % = DIVIDE([SL Count], [Total Working Days],0)
~~~

