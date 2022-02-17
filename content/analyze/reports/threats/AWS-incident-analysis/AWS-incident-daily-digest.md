# AWS Incident Daily Digest Report

The AWS Incident Daily Digest report displays Amazon GuardDuty and Network IDS incidents detected on the previous day for the selected Amazon Web Services (AWS) deployments and containers.   Use this report to evaluate daily AWS incidents by threat level, classification, and type.

For more information about incidents, see [Incidents](../../../incidents.md).

    You must configure Amazon GuardDuty for associated incidents to be displayed in Alert Logic console. For more information, see [Integrate Amazon GuardDuty Findings into Alert Logic Incidents](../../../../configure/integrate-guard-duty-findings.md).    
To access the AWS Incident Daily Digest report:

1. In the Alert Logic console, click the menu icon (![](../../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click **Threats**.
3. Under **AWS Incident Analysis**, click **VIEW**.
4. Click **AWS Incident Daily Digest**.

## Filter the report

Use the **View Previous Days (GMT)** drop-down menu to select which day to display activity for the report.

To refine your findings, filter your report by **Deployment Name**, **VPC**, **Container Image Name**, **Customer Account**, and **Detection Source**.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

### Filter the report using visuals

To refine your findings, click an item within a visual. To filter by multiple items, hold down **Ctrl** or **Command**, and then click each item in a visual that you want  to use to apply a filter. You can filter using visuals and items  selected in different sections. Click on an item again to remove a filter.

* **Bar graph example text**: To filter the report, click on a bar or hold **Ctrl** or **Command** and click  multiple bars to filter all sections by the selected Threat Level(s).
* **Line graph example text**: To filter the report, click on a point or choose an area on the line graph to filter the other sections by the selected week(s). Click a point or area on the line to filter all sections by your selection.
* **Pie chart**: To filter the report, select one or more sector to filter all sections on the page by your selection.
* **Histogram chart example text**: To filter the report, click on a bar or hold **Ctrl** or **Command** and click  multiple bars to filter all sections by the selected date(s).

## Number of Incidents (Daily) section

This section provides the total count of  incidents for the selected day.

![](../../../../Resources/Images/Reports/AWS-incident-analysis/number-incidents.png)

## Total Daily Change section

This section provides the count and percentage change between the selected day and the previous day.

![](../../../../Resources/Images/Reports/AWS-incident-analysis/daily-change.png)

## Total Targeted section

This section provides the total count of accounts, VPCs, and assets targeted in the incidents for the selected day.

![](../../../../Resources/Images/Reports/AWS-incident-analysis/total-targeted.png)

## Threat Level section

This section provides the count and percentages of incidents in each threat level for the selected day.

![](../../../../Resources/Images/Reports/incident-daily-digest/threat-level-daily.PNG)

## Incident by MITRE Tactic section

This section provides the count and percentages for each incident by MITRE Tactic in a color-coded bar graph for the selected day.

![](../../../../Resources/Images/Reports/incident-daily-digest/incident-MITRE-tactic.png)

## Incident by MITRE Technique section

This section provides the count and percentages for each incident by MITRE Technique in a color-coded bar graph for the selected day.

![](../../../../Resources/Images/Reports/incident-daily-digest/incident-MITRE-technique.png)

## Classification section

This section provides the count and percentages for each incident classification in a color-coded bar graph for the selected day.

![](../../../../Resources/Images/Reports/incident-daily-digest/classification-daily.PNG)

## Incident Type section

This section displays a bar graph of the daily incident count and percentages by each type for the selected day.

![](../../../../Resources/Images/Reports/incident-daily-digest/incident-type-daily.PNG)

## List of Incidents section

This section provides a complete list of incidents for the selected day with detailed information about Customer Account, Create Time, Detection Source, Incident ID, Summary, Threat Level, Classification, and Incident Type.

![](../../../../Resources/Images/Reports/AWS-incident-analysis/AWS-incident-list.png)