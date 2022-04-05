# Azure Incident Distribution Explorer Report

The Azure Incident Distribution Explorer report presents incident trends by  threat level, classification, and type for the selected date range. The report  presents the information in pie graphs and a series of histograms in each category for the selected date range.

For more information about incidents, see [Incidents](../../../incidents.md).

To access the Azure Incident Distribution Explorer report:

1. In the Alert Logic console, click the menu icon (![](../../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click **Threats**.
3. Under **Azure Incident Analysis**, click **VIEW**.
4. Click **Azure Incident Distribution Explorer**.

## Filter the report

To refine your findings, filter your report by  **Date Range**, **Customer Account**, **Detection Source**, **Deployment Name**, **Native Account ID**, **VPC**, **Container Image Name**, **Subnet**, **Security Group**, and **Top Tags**.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

## Total Incidents section

This section  provides the total  incident count for the selected filters and date range.

![](../../../../Resources/Images/Reports/incident-distribution-explorer/total-count.png)

## Incident Count by Threat Level and Trend for Selected Period section

This section provides the distribution of incidents by threat level for the selected date range.

Incident threat levels convey the severity of each incident raised for protected assets, which allows you to assess and prioritize the actions to take toward threat remediation. Alert Logic categorizes incidents with the following icons and colors:

* ![](../../../../Resources/Images/Icons/threat_critical_icon.png) Critical
* ![](../../../../Resources/Images/Icons/threat_high_icon.png) High
* ![](../../../../Resources/Images/Icons/threat_medium_icon.png) Medium
* ![](../../../../Resources/Images/Icons/threat_low_icon.png) Low
* ![](../../../../Resources/Images/Icons/threat_info_icon.png) Info

The pie chart presents the count and percentages for the  threat level category. The histogram presents the trend in daily incident counts by threat level. Use the scroll bar to the right of the histogram to view additional data.

![](../../../../Resources/Images/Reports/incident-distribution-explorer/incident-count-threat-trend.png)

## Incident Count by MITRE Tactic and Trend for Selected Period section

The section provides the distribution of incidents by MITRE Tactic for the selected date range. The pie chart  presents the count and percentages by MITRE Tactic. The histogram presents the daily trend of incident counts by MITRE Tactic. Use the scroll bar to the right of the histogram to view additional data.

![](../../../../Resources/Images/Reports/incident-distribution-explorer/incident-MITRE-tactic-trends.png)

## Incident Count by MITRE Technique and Trend for Select Period section

The section provides the distribution of incidents by MITRE Technique for the selected date range. The pie chart  presents the count and percentages by MITRE Technique. The histogram presents the daily trend of incident counts by MITRE Technique. Use the scroll bar to the right of the histogram to view additional data.

![](../../../../Resources/Images/Reports/incident-distribution-explorer/incident-MITRE-technique-trends.png)

## Incident Count by Classification and Trend for Selected Period section

The section provides the distribution of incidents by classification for the selected date range. The pie chart  presents the count and percentages for the  classification category. The histogram presents the daily trend of incident counts by classification. Use the scroll bar to the right of the histogram to view additional data.

![](../../../../Resources/Images/Reports/incident-distribution-explorer/incident-count-classification-trend.png)

## Incident Count by Incident Type and Trend for Selected Period section

The section provides the distribution of incidents by type for the selected date range. The pie chart  presents the count and percentages for the  type category. The histogram presents the daily trend of incident counts by type. Use the scroll bar to the right of the histogram to view additional data.

![](../../../../Resources/Images/Reports/incident-distribution-explorer/incident-count-type-trend.png)