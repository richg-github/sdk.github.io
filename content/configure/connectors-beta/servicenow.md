# Configure ServiceNow Webhook Connector

You can configure a webhook connector in the Alert Logic console  to send [notifications](../notifications.md) to ServiceNow in near real time. When  you set up a notification and subscribe a webhook connector, the connector sends the event to the target URL you configured and generates a service ticket  in ServiceNow automatically.

Alert Logic notifications alert you to threats, changes, and scheduled events in your environment so you can respond quickly. From the Alert Logic console, you can subscribe your ServiceNow webhook to receive:

* [Incident notifications](../notifications/incident.md)        —Generate a service ticket when incidents occur that meet specific criteria, such as escalated incidents.
* [Log correlation notifications](../notifications/log-correlation.md)        —Generate a service ticket when your log correlation rules trigger an incident or observation.
* [ Health Notifications](../notifications/health.md)        —Generate a service ticket when health exposures meet specific criteria.
* [Scheduled report notifications](../notifications/report.md)        —Generate a service ticket when Alert Logic generates a scheduled report  that is available for download.
* Scheduled search results

Complete the following steps to successfully generate service tickets  in ServiceNow:

1. [Select or Create a Connection Target](#SelectorCreateaConnectionTarget)
2. [Identify your ServiceNow target URL](#IdentifyyourServiceNowtargetURL)
3. [(Optional) Customize the sample payload template](#(Optional)Customizethepayloadtemplate)
4. [Create the ServiceNow webhook connector from the Alert Logic console](#CreatetheServiceNowwebhookconnector)
5. [Subscribe your webhook to receive notifications](#Subscribeyourwebhooktoreceivenotifications)

## Select or Create a Connection Target

Before creating a connector, you must first configure a connection target. Connection targets define common authentication path and credential references for external systems. For more information, see [Configure ServiceNow Connection Target](../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/servicenow.md).

## Identify your ServiceNow target URL

Before you create the webhook connector in the Alert Logic console, identify your ServiceNow instance name and make a note of it. In the Target URL field, you must replace "<myinstance>" with the ServiceNow instance to which you want to send Alert Logic security notifications.

## (Optional) Add additional header(s)

You may list a single HTTP header name-value pair required by the external system per line.

## (Optional) Customize the payload template

Decide which type of security information that you want Alert Logic to send to ServiceNow: Incident, Observation (of a log correlation), or a Scheduled Report Notification payload.

    If you want to send more than one payload type, you must configure a connector for each one. Because the payload is different, each payload type requires a separate connector instance.     
Alert Logic provides a payload template for an incident and an observation using JQ transformation. A payload template converts the Alert Logic security information to the format expected by ServiceNow. You can add or remove lines in the sample template to meet your workflow requirements and security goals. If you want to create a ServiceNow connector for scheduled report notifications, you will need to configure the payload template.

For definitions of the Alert Logic variables in the templates and the full  JSON that you can use to configure your payload template in JQ or JSON format, see:

* [Incident Schema](../connectors/incident.md)
* [Observation Schema](../connectors/observation.md)
* [Scheduled Report Notification Schema](../connectors/scheduled-report-notification-payload.md)

    For more information about JQ, see [JQ](https://stedolan.github.io/jq/#:~:text=jq) . A helpful website for converting JSON to JQ is [jq play](https://jqplay.org/).    ### Incident payload template

JQ Template

| 1 | { |
| 2 | "short_description": (.incident.summary + ". Incident ID: " + .humanFriendlyId), |
| 3 | "description": ("Customer: " + .customer + "\n" + "Deployment: " + .assets.al__deployment + "\n\n" + .incident.description + "\nIncident Link: " + .extra.incidentUrl), |
| 4 | "state": (if .customer_status.status == "open" then "1" elif .customer_status.status == "snoozed" then "3" elif .customer_status.status == "closed" then "7" else "8" end), |
| 5 | "severity": (if .incident_threat_rating == "Critical" then "1" elif .incident_threat_rating == "High" then "1" elif .incident_threat_rating == "Medium" then "2" else "3" end), |
| 6 | "urgency": (if .incident_threat_rating == "Critical" then "1" elif .incident_threat_rating == "High" then "1" elif .incident_threat_rating == "Medium" then "2" else "3" end) |
| 7 | } |

### Observation payload template

JQ Template

| 1 | { |
| 2 | "short_description": (.fields.summary + ". Observation ID: " + .fields.id), |
| 3 | "description": ("Recommendations:\n\n" + .fields.recommendations + "\n\nMessage:\n\n" + .fields.keys.message), |
| 4 | "severity": (if .fields.severity == "critical" then "1" elif .fields.severity == "high" then "1" elif .fields.severity == "medium" then "2" else "3" end) |
| 5 | } |

## Create the ServiceNow webhook connector from the Alert Logic console

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

If you receive a message that the connector was successfully tested, Alert Logic sends the payload template you configured and populates a service ticket in ServiceNow with sample data. Check ServiceNow to ensure the results are expected, and adjust the payload template if necessary.

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