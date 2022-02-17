# About Log Parsers in the Threat Intelligence Center

The Threat Intelligence Center provides a tabular list for the properties of each log parser available from Alert Logic.  Use the log parsers view in the Threat Intelligence Center to learn about log parser content. To learn more about the Threat Intelligence Center, see [Threat Intelligence Center (Beta)](../threat-intelligence-center.md).

## Learn about log parsers

Logs are messages that function as a ledger for activity generated by applications in a system. Limited format standards exist for log messages, which means that they must be parsed to identify and format activity of interest for each specific application. Alert Logic makes Log Parser content coverage visible in the Threat Intelligence Center so that you can easily track relationships among vendors, their applications and appliances, and whether Alert Logic parses logs generated by those applications and appliances. After log messages are parsed, analytics can evaluate the formatted, enriched log messages  to generate incidents and observations.

For more information about configuring log sources and collection, see [Log Sources](../../deploy/log-sources.md) and [Application Registry](../../configure/application-registry.md).

## Validate Log Message Type Coverage

By vendor

By appliance type

By application

##  Investigate content configuration requirements

You can  use the Threat Intelligence Center to verify that you have configured the collection sources required to detect specific threats in your deployments. You can find an analytic designed to evaluate a specific type of activity in the Threat Intelligence Center and check the telemetry property to see what data is required by the analytic.

    For example, you may find an analytic that uses Log telemetry to evaluate threat activity, which indicates that you need to have the collection configured for specific log sources on your assets for the analytic to evaluate the activity as an incident or observation. For more information on configuring specific log sources, see [Log Sources](../../deploy/log-sources.md) and [Application Registry](../../configure/application-registry.md).    ## Source information for Log Search

## Log parser properties details and use cases

Using the Threat Intelligence Center, you can review the properties of each Log Parser.

| Property | Description  | Use Cases | Examples |
|---|---|---|---|
| Date Added | Date that Alert Logic released the Log Parser. | Verify the release date of a log parser or cross-reference releases with your security posture history. | 3rd May 2017 20:07:32 GMT-5 |
| Log Message Type | Classification system for log messages. Each log parser analyzes one type of log message. Message type also functions as an identifier for the Log Parser. | Validate that you are collecting the correct data from a log source. Verify that Alert Logic analyzes specific types of log messages. You can search logs by message type collected in your environment using [Search: Log Messages](../log-message-search.md). | Cisco ASA Inbound TCP Traffic Blocked AWS EC2 Delete Vpc |
| Log Source | Name of the log source, often an application, that produces the log messages. For more information about configuring log sources, see [Log Sources](../../deploy/log-sources.md) and [Application Registry](../../configure/application-registry.md). | Determine if Alert Logic parses logs for a log source. Determine which log source to configure to make use of an Alert Logic log parser. | Cisco ASA Amazon AWS |
| Last Updated | Date that Alert Logic last updated the log parser. | Verify that Alert Logic log parsers are kept up to date or cross-reference updates with your security posture history. | 3rd Jun 2021 20:07:32 GMT-5 |
| Vendor | Name of the vendor or company that is associated with the log source. | Determine if Alert Logic parses logs for a specific vendor. | Cisco AWS |
| Log Source Classification | The Collector classification of each Log Source. See [Collectors Overview] for more information.Classification for the Log Source. | Verify Alert Logic coverage for log sources of specific types. View log source coverage by classification to determine which | Firewall/Router IaaS Email OS |
| Log Query |  | Validate that you are collecting/configured correctly for that analytic. |  |