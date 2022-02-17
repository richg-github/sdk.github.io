# HIPAA 164.308(a)(1)(ii)(D)—Information System Activity Review

The Health Insurance Portability and Accountability Act (HIPAA) Security Audit reports show available documentation and compliance artifacts that help you demonstrate compliance with requirements of the HIPAA Security Rule, as outlined in the HIPAA Audit Protocol.This report provides log review and log management incident information to help you demonstrate compliance with HIPAA 164.308(a)(1)(ii)(D).

**To access the HIPAA 164.308(a)(1)(ii)(D) report:**

1. In the Alert Logic console, click the menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), and then click ![](../../../Resources/Images/dashboard/validate-icon.png)**Validate**.
2. Click **Reports**, and then click  **Compliance**.
3. Under **HIPAA Security Audit**, click **VIEW**.
4. Click **HIPAA 164.308(a)(1)(ii)(D)—Information System Activity Review**.

## Filter the report

To refine your findings, you can filter your report by  date range and customer account, and deployment name.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

The report summary page displays two columns. **HIPAA Audit Protocol** lists each audit protocol inquiry for testing the selected HIPAA Security Rule requirement. **Available Documentation and Artifacts** describes, and contains links to, the documentation and compliance artifacts that this report can generate for each protocol.

This report is composed of four pages, this Summary page, the Log Review Summary page, the Log Review Incidents page, and the Log Management Incidents page. Each page includes filters to specify the scope of the information you need to collect.

## Available documentation and artifacts

This report provides documentation and artifacts that help you demonstrate the records of information system activities that were reviewed, such as audit logs, access reports, and security incident tracking reports.

In addition, this report includes links for quick access to the Incidents page in the Alert Logic console where auditors can search, observe, and review the details for Log Review and Log Management incidents.

### Log Review Summary page

The Log Review Summary page summarizes the daily distribution of incidents detected from audit logs and reviewed by Alert Logic analysts. You can use the information on this page to demonstrate that the daily audit log review process includes manual review of security events. You can also click the link for quick access to the Log Review incidents in the Alert Logic console where you can search for and view the details of the incidents.

To generate this report, from the Summary page, click **Log Review Summary page**. To refine your findings, you can filter this page by date range, customer account, and deployment name.

#### Status section

This section provides the status counts and percentages of total incidents that the Alert Logic Security Operations Center (SOC) analysts closed and escalated for the selected period.

![](../../../Resources/Images/Reports/Monthly-log-review/status.png)

#### Log Review Incidents by Day and Status section

This section provides a stacked histogram chart that displays the daily status counts  of total incidents that the SOC analysts closed and escalated for the selected period.

![](../../../Resources/Images/Reports/Monthly-log-review/incidents-by-day-and-status.png)

#### Log Review Incidents Summary Total section

This section displays the total, escalated, and closed incident counts for each type of log review summary category for the selected period.

For more information about the incidents during the selected period, click the **Monthly Log Review Report** to be redirected to the Monthly Log Review report. To learn more about the Monthly Log Review report, see [Monthly Log Review Report](../threats/log-review-analysis/monthly-log-review.md).

![](../../../Resources/Images/Reports/pci-requirement-10.6-incidents/log-review-incidents-summary-totals.png)

### Log Review Incidents page

The Log Review Incidents page provides the daily distribution of log in incidents reviewed by Alert Logic analysts. You can use the information on this page to demonstrate that the daily audit log review process includes manual review of security events. You can also click the link for quick access to the Log Review incidents in the Alert Logic console where you can search for and view the details of the incidents.

To generate this report, from the Summary page, click **Log Review Incidents page**. To refine your findings, you can filter this page by date range, customer account, and deployment name.

#### Incident Count by Day section

This section provides the daily incident count and the total count for  the selected period.

![](../../../Resources/Images/Reports/PCI-requirement-11.4/incident-count-by-day.png)

#### List of Incidents section 

The list displays Log Review incidents for the selected filters. The list is organized by customer account, date created, detection source, incident ID, and summary.

Click **Search Incidents** to be redirected to the Incidents Lists page, which contains more information about the incidents in the selected period.

![](../../../Resources/Images/Reports/pci-requirement-10.6-incidents/list-of-incidents-log-review.png)

### Log Management Incidents page

The Log Management Incidents page provides the daily distribution of Log Management incidents. You can use the information on this page to demonstrate that the daily review process includes an automated review of audit logs and access changes. You can also click the link for quick access to the Log Management incidents in the Alert Logic console where you can search for and view the details of the incidents.

To generate this report, from the Summary page, click **Log Management Incidents page**. To refine your findings, you can filter this page by date range and customer account.

### Filter the report using drop-down menus

By default, Alert Logic includes **(All)** filter values in the report.

**To add or remove filter values: **

1. Click the drop-down menu in the filter, and then select or clear values.
2. Click **Apply**.

#### Incident Count by Day section

This section provides the daily incident count and the total count for  the selected period.

![](../../../Resources/Images/Reports/PCI-requirement-11.4/incident-count-by-day.png)

#### Threat Level section

This section displays the incident threat levels, the incident count for each threat level, and the percentage for each incident threat level in a color-coded bar graph in the selected filters. The threat levels are the following:

* Critical: May represent a successful attack or breach
* High: Requires immediate attention
* Medium: Requires closer observation and monitoring
* Low: Common violations and events
* Info: No threat detected or used for correlation

![](../../../Resources/Images/Reports/PCI-requirement-11.4/threat-level.png)

#### Classification section 

This section displays the classifications of incidents, the count for each incident classification, and the percentage for each incident classification in a color-coded bar graph in the selected filters.

![](../../../Resources/Images/Reports/PCI-requirement-11.4/classification.png)

#### Incident Type section

This section displays the types of incidents, the count for each incident types, and the percentage for each incident type in a color-coded bar graph in the selected filters.

![](../../../Resources/Images/Reports/PCI-requirement-11.4/incident-type.png)

#### List of Incidents section

The list displays Log Management incidents for the selected filters. The list is organized by customer account, date created, detection source, incident ID, summary, threat level, classification, and incident type.

Click **Search Incidents** to be redirected to the Incidents Lists page, which contains more information about the incidents in the selected period.

![](../../../Resources/Images/Reports/pci-requirement-10.6-incidents/list-of-incidents.png)