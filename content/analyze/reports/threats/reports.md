# Threats Reports 

The **REPORTS** tab in the Alert Logic console provides access to data related to exposures and incidents Alert Logic found within your deployments. You can also view data related to your product usage within your accounts. For information on all the available report groups, see [Reports Guide](../reports.md).

The Threats reports provide convenient access to analysis, statistics, assessments, and trending data related to threats and incidents detected from your subscribed products and services. Alert Logic provides Threats reports within the following categories:

* [Incident Analysis](#incidentAnalysis) — Provides valuable insights and trending data for incidents created from all subscribed detection sources (Network IDS, Log Management, Amazon GuardDuty).
* [AWS Incident Analysis ](#AWSincident)— Provide valuable insights and trending data for incidents discovered in your AWS environments from Network IDS and incidents generated by Amazon GuardDuty security findings.
* [Azure Incident Analysis ](#Azureincident)— Provides valuable insights and trending data for incidents in your Azure environments created from Network IDS detection sources.
* [Incident Account Summary](#account) — Provide the current distribution and trending data for incidents detected across your customer accounts.
* [Log Review Analysis](#Log)— Provide valuable insights and trending data for incidents that are reviewed daily by Alert Logic security analysts.
* [ Web Application Analysis](#Web) — Provide valuable summary, distribution, and trending data for policy violations from your Alert Logic Managed Web Application Firewall (WAF).
* [Event Analysis](#Event) — Provides valuable insights and trending data for security events that were detected and processed in your environment from Network IDS sources.

To access the Threats reports, in the Alert Logic console,  click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**. Click **Reports**, and then click **Threats**.

Each report allows you to share its data by email, or download the report as an image, data, crosstab, PDF, or PowerPoint files. To learn how to download reports, see [Report Download Option](../download-option.md).

You can also schedule a report to run periodically and subscribe users or an integration (such as a webhook) to receive a notification when the report is generated.   From the Downloads tab on the Reports page, you can download and manage reports generated from your schedules. For more information, see [Scheduled Reports and Notifications](../../../configure/notifications/report.md).

## Filtering reports

You can filter your reports quickly to refine your results and generate relevant information you need. Each report has a set of filters located at the top that you can select or clear for the filters you want to see. Alert Logic also allows you to add or remove some or all values in a filter you want to see. Some reports also support filtering by visuals.

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

### Incident Analysis

You can run the following reports that provide information about incidents in your  environments created from all subscribed detection sources (Network IDS, Log Management, Web App IDS, Amazon GuardDuty):

* **Monthly Incident Analysis**: Provides visibility into threats and incidents in your environment, including incident statuses, threat levels, classification, daily incident count, and top ten lists for the selected month.To learn more about this report, see [Monthly Incident Analysis ](incident-analysis/monthly-incident.md).
* **Weekly Incident Analysis**: Provides visibility into threats and incidents in your environment, including incident statuses, threat levels, classification, daily incident count, and top ten lists for the selected week. To learn more about this report, see [Weekly Incident Analysis](incident-analysis/weekly-incident.md).
* **Incident Daily Digest:** Presents the incidents detected on the previous day for the selected detection types. You can view visualizations and list of incidents by threat level, by classification, or by incident type. You can filter the report by detection source, status, previous days, or customer account. For more information, see [Incident Daily Digest](incident-analysis/incident-daily-digest.md).
* **Incident Daily Digest Trends:**  Presents a histogram chart that allows you to review trends in the daily incident digest results for a selected date range. You can view visualizations and list of incidents by threat level, by classification, or by incident type. For more information, see [Incident Daily Digest Trends](incident-analysis/incident-daily-digest-trends.md).
* **Incident Distribution Explorer:** Provides incident trends by detection source, status, threat level, classification, type, and sub-type for the date range. The report  presents the information in pie graphs and a series of histograms in each category for the selected date range. For more information, see [Incident Distribution Explorer](incident-analysis/incident-dist-explorer.md).
* **Incident Target Explorer:** Displays the top 10 targets, with visualizations and lists of incidents by threat level, by classification, or by incident type. You can filter the report by detection source, status, previous days, or customer account. For more information, see [Incident Target Explorer Report](incident-analysis/incident-target-explorer.md).
* **Incident Attacker Explorer:** Displays the top 10 attackers and geolocations, with visualizations and lists of incidents by threat level, by classification, or by incident type. You can filter the report by detection source, status, previous days, or customer account. For more information, see [Incident Attacker Explorer](incident-analysis/incident-attacker-explorer.md).
* **Incident Workflow Explorer:**Evaluates workflow actions performed in response to incidents, including total incidents by action count and percentage, total daily workflow actions, closed and updated incidents by reason, and trends. You can filter the report by detection source, status, previous days, or customer account. For more information, see [Incident Workflow Explorer Report](incident-analysis/incident-workflow-explorer.md).

### AWS Incident Analysis 

You can run the following reports that provide information about incidents in your AWS environments generated by GuardDuty and Network IDS:

* **AWS Incident Daily Digest:** Displays the incidents received the previous day for the selected deployments. You can view the List of Incidents by threat level, classification type, or by GuardDuty findings. You can filter this report by deployment, VPC, container image, and detection source. For more information, see [AWS Incident Daily Digest Report](AWS-incident-analysis/AWS-incident-daily-digest.md).
* **AWS Incident Daily Digest Trends:** Allows you to view a histogram chart that displays the incident daily digests for specified date range, and by deployment, VPC, container image, and detection source. For more information, see [AWS Incident Daily Digest Trends](AWS-incident-analysis/AWS-incident-daily-digest-trends.md).
* **AWS Incident Distribution Explorer:** Displays incidents by threat level, classification, and incident type for a specified time period. You can filter the report by date range, detection source, deployment, and AWS account ID, container image, subnet, security group, and tag. For more information, see [AWS Incident Distribution Explorer](AWS-incident-analysis/AWS-incident-dist-explorer.md).
* **AWS Targeted Deployment Explorer:** Displays the GuardDuty and Network IDS incident distribution for a specified target (AWS account ID, regions, VPC, container image, security group or subnet), filtered by AWS account ID, date range, detection source, deployment, and AWS asset within your deployments. For more information, see [AWS Targeted Deployment Explorer](AWS-incident-analysis/AWS-targeted-deployment-explorer.md).
* **AWS Targeted Deployment Trends:** Displays an interactive graph depicting incident distribution for a specified time period, by account ID, AWS region, and AWS asset. For more information, see [AWS Targeted Deployment Trends](AWS-incident-analysis/AWS-targeted-deployment-trends.md).

### Azure Incident Analysis 

You can run the following reports that provide information about incidents in your Azure environments generated by Network IDS

* Azure **Incident Daily Digest:** Displays Network IDS incidents received the previous day for the selected deployments. You can view the List of Incidents by threat level, classification, or incident type. You can filter this report by deployment, VNet, container image, and detection source. For more information, see [Azure Incident Daily Digest Report](Azure-incident-analysis/Azure-incident-daily-digest.md).
* Azure **Incident Daily Digest Trends:** Allows you to view a histogram chart that displays the Azure daily incident digests for specified date range, customer account, by deployment, VNet, container image, and detection source. For more information, see [Azure Incident Daily Digest Trends Report](Azure-incident-analysis/Azure-incident-daily-digest-trends.md)
* Azure **Incident Distribution Explorer:** Displays incidents by threat level, classification, and incident type for a specified time period. You can filter the report by date range, customer account, detection source, deployment, native account ID, container image name, subnet, security group, and tag. For more information, see [Azure Incident Distribution Explorer Report](Azure-incident-analysis/Azure-incident-dist-explorer.md).
* Azure **Targeted Deployment Explorer:** Displays the Network IDS incident distribution for a specified target (Native Account ID, regions, VNet, container image, security group or subnet), filtered by Native Account ID, date range, detection source, deployment, and other Azure assets within your deployments. For more information, see [Azure Targeted Deployment Explorer](Azure-incident-analysis/Azure-targeted-deployment-explorer.md).
* Azure **Targeted Deployment Trends:** Displays an interactive graph depicting the Network IDS incident distribution for a specified time period, by Native Account ID, VNet, containers,  and other Azure assets within your deployment. For more information, see [Azure Targeted Deployment Trends](Azure-incident-analysis/Azure-targeted-deployment-trends.md).

### Incident Account Summary

You can run the following reports that provide the current distribution and trending data for incidents detected across your customer accounts and deployments.

* **Weekly Incident Account Summary**: Provides the current weekly distribution and trending data for incidents detected across your customer accounts and deployments by top incident count, threat level, count by day and threat level, detection source, escalation status, type, sub-type, top attackers, and top targets. For more information, see [Weekly Incident Account Summary](incident-account-summary/weekly-incident-account.md)
* **Monthly Incident Account Summary**: Provides the current monthly distribution and trending data for incidents detected across your customer accounts and deployments by top incident count, threat level, count by week and threat level, detection source, escalation status, type, sub-type, top attackers, and top targets. For more information, see [Monthly Incident Account Summary](incident-account-summary/monthly-incident-account.md).

### Log Review Analysis

You can run the following report that provides insight into your Log Review incidents created in the Incidents page:

* **Monthly Log Review**: Provides a monthly summary analysis of your Log Review incidents, including count and percentage of total incidents of each status, a daily histogram chart, and a comparison to the previous month. To learn more about this report, see [Monthly Log Review Report](log-review-analysis/monthly-log-review.md).

###  Web Application Analysis

You can run the following reports that provide information for policy violations from your inline Alert Logic Managed Web Application Firewall (WAF).

* WAF** Violation Explorer:** Provides visibility into blocked WAF requests and attempted web app attacks, including total and blocked WAF policy violations counts, violations by day, operating mode, risk level, attack class, and type. To learn more about this report, see [WAF Violation Explorer Report](web-application-analysis/waf-violation-explorer.md).
* **WAF Violation Trends:** Provides insights into patterns in your WAF violations, including violation distribution and trends categorized by action, risk level, attack class, violation type, response code, method, and protocol. To learn more about this report, see [WAF Violation Trends](web-application-analysis/waf-violation-trends.md).

### Event Analysis

You can run the following reports that provide insights for security events that were processed from Network IDS sources:

* Network IDS** Events Explorer**: Provides visibility into Network IDS events processed in your environment, including events per day, visualizations by payload and classification, top signatures, and top source and destination IP addresses and ports. To learn more about this report, see [Network IDS Events Explorer](event-analysis/network-ids-events-explorer.md).
* **Monthly Event Analysis**: Provides visibility into Network IDS events processed in your environment, including event classification, top signatures, and events per day for the selected month.To learn more about this report, see [Monthly Event Analysis](event-analysis/monthly-event-analysis.md).
* **Weekly Event Analysis**: Provides visibility into Network IDS events processed in your environment, including event classification, top signatures, and events per day for the selected weekly.To learn more about this report, see [Weekly Event Analysis](event-analysis/weekly-event-analysis.md).
* Network IDS** Events Explorer**: Provides visibility into Network IDS events processed in your environment, events per day, visualizations by payload and classification, and top signatures. To learn more about this report, see [Network IDS Events Explorer](event-analysis/network-ids-events-explorer.md).
* **Top Event Sources and Destinations**: Lists the top source and destination IP addresses and ports for IDS events in your environment. To learn more about this report, see [Top Event Sources and Destinations](event-analysis/top-sources-destinations.md).