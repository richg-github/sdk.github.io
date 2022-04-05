# Configure a Jira Connection Target

A Jira connection target securely stores reusable authentication credential and URL path information for integrations with Jira.

Complete the following steps to  configure a connection target for Jira:

1. [Identify your Jira base target URL](#IdentifyyourJirabasetargetURL)
2. [Create an Atlassian API token](#CreatanAtlassianAPItoken)
3. [Generate an Authorization header](#GenerateanAuthorizationheader)
4. [(Optional) Add custom header(s)](#(Optional)Addcustomheader(s))
5. [Use the connection target in connectors and playbooks](#Usetheconnectiontargetinconnectorsandplaybooks)

## Identify your Jira base target URL

Identify your Jira instance name. In the Base URL field, you must replace "<myinstance>" in the default URL provided in the Alert Logic console with the Jira instance  you want to target.

## Create an Atlassian API token

For    connection targets, the authorization header <password> must be an API token generated in your Atlassian account. For directions on how to generate and use an API token from your Atlassian account, see [Create an API token](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/).

## Generate an Authorization header

Jira requires an HTTP Authorization request header. You can use the following instructions for your operating system to generate the header.

The command requires a valid Jira user name and password, and it encodes the credentials with base64. To construct the header, you enter the word "Basic" (which is the Authorization header type), a space, and then the  base64-encoded credentials.

Alert Logic stores your Authorization header securely when you save the connector.

**To generate the header on Linux and Mac OS X:**

1. In the command line, type the following command, including the single quotation marks:
<kbd>echo -n '&amp;lt;user_name&amp;gt;:&amp;lt;password&amp;gt;' | base64</kbd>
where you must replace <user_name> and <password> with a valid user name and password  for Jira.
2. Copy the following string, which you must enter in the **Authorization Header** field when you create the connector:
<kbd>Basic &amp;lt;resulting_base64_encoded_string&amp;gt;</kbd>

    If the user name is "admin" and the password is "testpassword" for example, the command is: 

<kbd>echo -n 'admin:testpassword' | base64</kbd>

 and the command produces this output: 

<kbd>YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

 So, in the Authorization Header field, you would paste:

<kbd>Basic YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

**To generate the header in Windows PowerShell:**

1. In the command line, type the following commands, including the quotation marks:
<kbd>$auth  = [System.Text.Encoding]::UTF8.GetBytes("&amp;lt;user_name&amp;gt;:&amp;lt;password&amp;gt;")</kbd>
where you must replace <user_name> and <password> with a valid user name and password for Jira.
<kbd>[System.Convert]::ToBase64String($auth)</kbd>
2. Copy the following string, which you must enter in the **Authorization Header** field when you create the connector:
<kbd>Basic &amp;lt;resulting_base64_encoded_string&amp;gt;</kbd>

    If the user name is "admin" and the password is "testpassword" for example, the commands are:

<kbd>$auth  = [System.Text.Encoding]::UTF8.GetBytes("admin:testpassword")</kbd>

<kbd>[System.Convert]::ToBase64String($auth)</kbd>

and the command produces this output: 

<kbd>YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

So, in the Authorization Header field, you would paste:

<kbd>Basic YWRtaW46dGVzdHBhc3N3b3Jk</kbd>

## (Optional) Add custom header(s)

You may list a single HTTP header name-value pair required by the external system per line. By default, a JSON content-type header is included to assist processing:

<kbd>Content-Type: application/json</kbd>

## Create the Jira connection target from the Alert Logic console

1. In the Alert Logic console, click the navigation menu icon (![](../../../Resources/Images/dashboard/menu-icon.png)), click ![](../../../Resources/Images/dashboard/configure-icon.png)**Configure**, and then click **Connectors**.
2. Click on the **Connection Targets** tab.
3. On the Connection Targets page, click the add icon (![](../../../Resources/Images/Icons/cdAddPlus.png)), and then click **Jira**.
4. On the Create a Jira Connection Target page, type a descriptive name for the connection target —for example, "Jira Connection Target".
5. In  **Base URL**, use the URL you identified earlier.
6. Activate the connection target if you want to use it, or leave it inactive to save the connection target for later.
7. Click **SAVE**.

## Use the connection target in connectors and playbooks

After you save the connection target, the last step is to set up a connector or automated response playbook. For more information on connectors, see [Connectors Configuration Guide](../../../Z-Sandbox/bbaskin/connectors-beta/connectors.md). For more information on automated response, see [Get Started with Automated Response (Beta)](../../../respond/automated-response.md).

## Manage connection targets

You can view the list of connection targets and edit or delete an existing one. For more information, see [Manage Connection Targets](../../../Z-Sandbox/bbaskin/connectors-beta/connection-targets/manage-connection-targets.md).