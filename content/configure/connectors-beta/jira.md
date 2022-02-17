# Configure Jira Webhook Connector

You can configure a webhook connector in the Alert Logic console  to send [notifications](../notifications.md) to Jira in near real time. When  you set up a notification and subscribe a webhook connector, the connector sends the event to the target URL you configured and generates an issue  in Jira automatically.

Alert Logic notifications alert you to threats, changes, and scheduled events in your environment so you can respond quickly. From the Alert Logic console, you can subscribe your Jira webhook to receive:

* [Incident notifications](../notifications/incident.md)        —Generate an issue when incidents occur that meet specific criteria, such as escalated incidents.
* [Log correlation notifications](../notifications/log-correlation.md)        —Generate an issue when your log correlation rules trigger an incident or observation.
* [ Health Notifications](../notifications/health.md)        —Generate an issue when health exposures meet specific criteria.
* [Scheduled report notifications](../notifications/report.md)        —Generate an issue when Alert Logic generates a scheduled report  that is available for download.
* Scheduled search results

Complete the following steps to successfully generate issues  in Jira:

1. [Select or Create a Connection Target](#SelectorCreateaConnectionTarget)
2. [Identify your Jira target URL](#IdentifyyourJiratargetURL)
3. [(Optional) Add additional header(s)](#(Optional)Addadditionalheader(s))
4. [Customize the payload template](#Customizethesamplepayloadtemplate)
5. [Create the Jira webhook connector from the Alert Logic console](#CreatetheJirawebhookconnector)
6. [Subscribe your webhook to receive notifications](#Subscribeyourwebhooktoreceivenotifications)

## Select or Create a Connection Target

Before creating a connector, you must first configure a connection target. Connection targets define common authentication path and credential references for external systems. For more information, see [Configure a Jira Connection Target](../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/jira.md).

## Identify your Jira target URL

To create a ticket in Jira, you will use the default target URL provided in the Alert Logic console. Advanced API integration targeting can be done by modifying the target URL. See Jira documentation for advanced integration support.

## (Optional) Add additional header(s)

You may list a single HTTP header name-value pair required by the external system per line.

## Customize the payload template

Decide which type of security information that you want Alert Logic to send to Jira: Incident, Observation (of a log correlation), or a Scheduled Report Notification payload.

    If you want to send more than one payload type, you must configure a connector for each one. Because the payload is different, each payload type requires a separate connector instance.     
Alert Logic provides a payload template for an incident and an observation using JQ transformation. A payload template converts the Alert Logic security information to the format expected by Jira. You can add or remove lines in the sample template to meet your workflow requirements and security goals. You must replace placeholder information in angle brackets with valid values. If you want to create a Jira connector for scheduled report notifications, you will need to configure the payload template.

For definitions of the Alert Logic variables in the templates and the full  JSON that you can use to configure your payload template in JQ or JSON format, see:

* [Incident Schema](../connectors/incident.md)
* [Observation Schema](../connectors/observation.md)
* [Scheduled Report Notification Schema](../connectors/scheduled-report-notification-payload.md)

    For more information about JQ, see [JQ](https://stedolan.github.io/jq/#:~:text=jq). A helpful website for converting JSON to JQ is [jq play](https://jqplay.org/).    ### Incident payload template

JQ Template

| 1 | { |
| 2 | "fields": { |
| 3 | "reporter": { |
| 4 | "id": "<REPORTER ID>" |
| 5 | }, |
| 6 | "issuetype": { |
| 7 | "name": "Task" |
| 8 | }, |
| 9 | "project": { |
| 10 | "key": "<PROJECT KEY>" |
| 11 | }, |
| 12 | "summary": .incident.summary, |
| 13 | "description": { |
| 14 | "type": "doc", |
| 15 | "version": 1, |
| 16 | "content": [ |
| 17 | { |
| 18 | "type": "paragraph", |
| 19 | "content": [ |
| 20 | { |
| 21 | "text": .incident.description, |
| 22 | "type": "text" |
| 23 | } |
| 24 | ] |
| 25 | }, |
| 26 | { |
| 27 | "type": "paragraph", |
| 28 | "content": [ |
| 29 | { |
| 30 | "type": "text", |
| 31 | "text": "Link to the incident", |
| 32 | "marks": [ |
| 33 | { |
| 34 | "type": "link", |
| 35 | "attrs": { |
| 36 | "href": .extra.incidentUrl |
| 37 | } |
| 38 | } |
| 39 | ] |
| 40 | } |
| 41 | ] |
| 42 | } |
| 43 | ] |
| 44 | }, |
| 45 | "priority": { |
| 46 | "name": (if .incident_threat_rating == "Critical" then "Highest" elif .incident_threat_rating == "High" then "High" elif .incident_threat_rating == "Medium" then "Medium" else "Low" end) |
| 47 | } |
| 48 | } |
| 49 | } |

### Observation payload template

JQ Template

| 1 | { |
| 2 | "fields": { |
| 3 | "reporter": { |
| 4 | "id": "<REPORTER ID>" |
| 5 | }, |
| 6 | "issuetype": { |
| 7 | "name": "Task" |
| 8 | }, |
| 9 | "project": { |
| 10 | "key": "<PROJECT KEY>" |
| 11 | }, |
| 12 | "summary": .fields.summary, |
| 13 | "description": { |
| 14 | "type": "doc", |
| 15 | "version": 1, |
| 16 | "content": [ |
| 17 | { |
| 18 | "type": "paragraph", |
| 19 | "content": [ |
| 20 | { |
| 21 | "text": ("Description: " + .fields.desc), |
| 22 | "type": "text" |
| 23 | }, |
| 24 | { |
| 25 | "text": ("Recommendations: " + .fields.recommendations), |
| 26 | "type": "text" |
| 27 | }, |
| 28 | { |
| 29 | "text": ("Class: " + .fields.class), |
| 30 | "type": "text" |
| 31 | }, |
| 32 | { |
| 33 | "text": ("Subclass: " + .fields.subclass), |
| 34 | "type": "text" |
| 35 | } |
| 36 | ] |
| 37 | } |
| 38 | ] |
| 39 | }, |
| 40 | "priority": { |
| 41 | "name": (if .fields.severity == "critical" then "Highest" elif .fields.severity == "high" then "High" elif .fields.severity == "medium" then "Medium" else "Low" end) |
| 42 | } |
| 43 | } |
| 44 | } |

## Create the Jira webhook connector from the Alert Logic console

After you note your  instance name, generate the Authorization header, and optionally customize  the payload template, the next step is to create the webhook in the Alert Logic console  and test the payload.

**To create a  webhook connector**:

1. In the Alert Logic console, click the navigation menu icon (![](../../Resources/Images/dashboard/menu-icon.png)), click ![](../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. On the Connectors page, click the add icon (![](../../Resources/Images/Icons/cdAddPlus.png)), and then click ****.
3. On the Create a  Connector page, type a descriptive name for the webhook connector—for example, " Webhook Connector for Incidents."
4. Select or create a connection target.
5. In **Additional Header(s)**, leave the information as is. The field is prepopulated with the custom headers that  requires.
6. Choose the **Payload Type**, which is the type of Alert Logic security information that you want to send: **Incident**, **Observation** (of a log correlation), or **Scheduled Report Notification**.
7. Choose the format of the payload template you customized earlier: **JSON**  or **JQ**.
8. Choose an HTTP connector verb for the connector payload. If you are unsure, leave it as the default verb.
9. Enter the payload template that you customized.
      A red bar next to a line indicates a syntax error. Code with errors is underlined with a jagged red line. You can hover your pointer over the underlined code to view a tip about the error.       11. Click **TEST** to send a test webhook request to the  URL provided. For more information, see [Connector test results](#Connectortestresults).
12. If your webhook connector sent the test event to the  URL successfully, click **SAVE**.

### Connector test results

If you receive a message that the connector was successfully tested, Alert Logic sends the payload template you configured and populates an issue in Jira with sample data. Check Jira to ensure the results are expected, and adjust the payload template if necessary.

If the test is unsuccessful, Alert Logic displays an error message. For server response errors, you can use the error code and message that Alert Logic passes through to troubleshoot the issue. Alert Logic also informs you if your JSON or JQ payload template contains syntax errors.

## Subscribe your webhook to receive notifications

After you test and save the connector configuration, the last step is to set up your notification criteria and subscribe the webhook.

You can set up and manage a notification of any type directly from the Notifications page. For more information, see [Manage Notifications](../notifications/manage.md). You can create notifications from other pages according to notification type:

* For incidents, you can also create a notification from the Incidents page. For more information, see [Incident Notifications](../notifications/incident.md).
* For observations, you can also create a notification   from the Search page (Log Search tab or Correlations tab) during the process of creating the correlation or by editing an existing correlation listed on the Correlations tab. For more information, see [Correlations and Notifications](../notifications/log-correlation.md) and [Observation Notifications](../notifications/observation.md).
* For health exposures, you can also create a notification from the Health page. For more information, see [Health](../../analyze/health.md).
* For scheduled reports, you can also schedule the report and subscribe notification recipients from the Reports page. For more information, see [Scheduled Reports and Notifications](../notifications/report.md).
* For scheduled File Integrity Monitoring (FIM) searches, you can schedule a search and subscribe notification recipients from the Notifications page. For more information, see [File Integrity Monitoring Search Notification](../notifications/fim-search.md).

## Manage your connectors

You can view the list of connectors and edit or delete an existing one. For more information, see [Manage Connectors](../connectors/manage-connectors.md).