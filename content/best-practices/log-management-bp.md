# Log Management Best Practices

Configuring log management systems has become more complex as elaborate networks and increased regulatory requirements demand a more complex log management setup. Log management now extends beyond simple data collection; it encompasses normalization, analysis, reporting, and disaster-proof archival processes. The expansion of IT infrastructure into hosted and cloud deployments means you have more data to manage, and that data resides in a variety of environments.

These emerging challenges require that you configure your log management practices to focus on several key areas:

* Collect the appropriate data. Consider all the sources of log data in your environment, as well as those required to meet compliance mandates, alert you to suspicious activity, and provide valuable forensic data.
* Make log data usable in a normalized, searchable format.
* Review and analyze log data regularly. Log data will not help you achieve your goals if you do not examine it regularly. For compliance purposes, doing so is a requirement.

You can use the Alert Logic console to configure log sources and log searches. For more information see [Log Sources](../deploy/log-sources.md) and [Search: Log Messages](../analyze/log-message-search.md).

## Which logs to collect

To meet regulatory compliance standards, all logs must be collected—not just the security logs. For example, operating system logs and application logs often contain security-related information and information about events that may not initially appear security related. Organizations must consider the potential value of each possible log source. Consider the following log types for collection.

### Anti-malware software

Examples of anti-malware software include endpoint detection and response, anti-virus, anti-spyware, and rootkit detectors. These logs could include information like indicators of malware detection, disinfection attempt results, file quarantines, when file system scans were last performed, when anti-virus signature files were last updated, and when software upgrades took place.

### Applications

The information logged by various applications can vary widely and may include account changes, user authentication attempts, use of privileges, usage details, client and server activity, configuration changes, major system failures, and more. Application logs can be more valuable when network communications are encrypted; however, application logs are often proprietary formats.

### Authentication servers

Directory servers and single signon servers typically log each authentication attempt, including the originating user ID, destination system or application, date and time info, and success/failure details.

### Cloud services platforms

The popularity of cloud services platforms like Amazon Web Services (AWS), and Microsoft Azure means you must be able to collect logs from those services.

* AWS logs messages generated by the AWS CloudTrail service, and logs S3 details about single access requests like the requester, bucket name, request time, request action, response status, and any error codes.
* Azure records log data for operations performed on Azure resources, detailed error information for HTTP failure status codes, failed requests, or HTTP transactions using the W3C extended log file format.
* Microsoft Office 365 records activity logs that provide information including administrative, user, and policy actions.
* Microsoft Azure Event Hubs can be configured to collect Azure Active Directory logs, Diagnostic Activity logs, Security Center logs, and SQL Audit logs.

### Firewalls

Some firewalls are perimeter focused and general in nature, while others are very application-specific or single-host (personal) focused. Firewalls cannot only block activity based on policy, they can also inspect content and ensure the state and integrity of permitted connections. Firewalls have numerous capabilities, and their logs can be very detailed and informative.

### Intrusion prevention systems 

These systems record detailed information about suspicious behavior and detected attacks as well as actions taken to halt malicious activity in progress. Some intrusion protection systems, such as file integrity systems, run periodically instead of continuously, so they generate logs in batches rather than an ongoing basis.

### Network access control servers

Network access control can operate for both internal and external hosts connecting to the internal network. At the time of connect, the network access control service determines the hosts’ security posture, and hosts failing to adhere to the defined policy are quarantined onto a separate virtual local area network (VLAN ) segment. Network admission control (NAC) servers log information like network addresses and user identity for successful/permitted network connections and unsuccessful quarantined network connections.

### Network devices (routers, switches, etc)

You can configure routers to block certain types of traffic. You can also configure network devices to log detailed connection activity but these devices are typically configured to log very lightly and traditionally contained information about the source, destination, and the type of communication allowed or denied. Newer or more security-focused devices can provide deeper insights into the contents of network traffic as well.

Enabling detailed logging can result in high log volume and impose extra load on network devices. Carefully select the type of logging for each device, based on location and the expected utility of the data in your environment.

### Operating systems

Servers, workstations, and network devices run varied operating systems, and the host administrator typically controls logging. The types of events, as well as whether to log only successful or only failed events, or both, can be controlled.

These log entries typically contain information about service starts and stops, authentication attempts, file accesses, security policy changes, account changes, permission and privilege changes, and use of privileges. Operating system logs can also contain information from security software and system applications. The logs can identify suspicious activity involving a particular host.

### Remote access software 

Virtual private networks (VPNs) are the most popular type of secured remote access solutions, and they log both successful and failed connection attempts. The logs include details like the date and time each user connects and disconnects, and the types and amount of data sent and received during the connected session.

### Vulnerability management software

Vulnerability management software includes both vulnerability scanning and patch management software. These types of software typically run on an occasional basis and log batches of log entries that include information about scanned hosts and devices. This information includes:

* Configuration
* Missing software updates
* Identified vulnerabilities
* Patch and scan currency downloads

### Web proxies

Web proxies are the intermediate hosts that provide access to websites. Web proxies can also be used to restrict web access and to add a layer of protection between the user and external websites. Web proxy logs record user activity and the URLs accessed by specified users.

Each type of log contains varied information, and this information is in different formats. Depending on the circumstances, different log sources can be of more or less value. It should also be noted that if administrative privileges are not properly maintained and the logs secured, then the logs could be manipulated or altered. It is important to understand and limit such privileges and access to logged data as well.

## Log management challenges

Many compliance mandates, such as PCI DSS 3.1, require not only that you collect all logs, but that they be reviewed regularly, are searchable, and are stored in their original, unaltered, raw form for mandate-specific timeframes.

Logs can also be extremely useful in identifying security incidents, policy violations, fraudulent activity, and operational problems shortly after they occur. They are extremely valuable when performing audits, forensic analysis, internal investigations, establishing baselines, and identifying operational trends and long-term problems. However, the infinite variety of log data formats makes it impossible to utilize the data without data normalization.

It is reasonable to assume that the variety of log data sources and the volume of data will always increase. Compounding this challenge is the variability of data formats and distributed nature of these sources; in addition, every network infrastructure is in a constant state of change, with new systems, applications, users, and devices every day of the year.

This creates a variety of specific challenges for log management efforts. These challenges can be broken down into three areas: collection, analysis and review, and archival.

### Collection

When we discuss log data, we are discussing a wide and ever-changing range of data sets that must be accounted for.

* Log data is varied. Not only do systems, applications, and network devices have their own logs with varying types of specific data that are captured, but a single log source can have multiple logs to be captured. For example, applications often have multiple log files, each containing a specific type of data.
* Log data sources are distributed. Data sources may be located within internal on-premises infrastructure, collocated in a data center, hosted with a managed hosting provider, or located in the cloud. The infrastructure may be managed separately or in a hybrid environment. Log collection must span all of these environments.
* Log data sources change constantly. A new system, application, or network device may be brought online at any time, and begin generating new log data. Cloud instances may be launching for days or hours and then terminating. A log management solution must account for these changes, or else 100% log collection will not be possible. Otherwise, an organization risks discovering that a log source has not been collected after weeks or months, possibly in response to an auditor’s questions.
* Log data may contain sensitive information, such as excerpts from emails, user names and passwords. This raises security and privacy concerns that necessitate proper log data security. Logs improperly secured when being transported to any centralized collection system are susceptible to intentional or unintentional alteration or destruction.

### Analysis and review

Analysis and review of log data presents two significant challenges: regular review of log data, and the varying formats of log data.

Regular log review is a valuable practice for any organization, and is a requirement of many compliance mandates. Typically, system administrators have been responsible for reviewing and analyzing log data, but this has usually been a lower priority than other activities, such as more strategic business projects. Rapid-response situations, such as performance issues, vulnerability remediation, and security incident response and investigation, also tend to take priority over log review. The result? Log management projects are never started, or at best, linger unfinished.

Log contents vary enormously. Some logs are designed for humans to read and others simply are not; some logs use standard formats, while others use proprietary formats. Some log formats are comma separated, some are space delimited, and still others use symbols or other character delimiters between the fields within a single log message.

Each log entry, or message, contains certain defined pieces of information, such as a host IP address or username. Each log source records information considered important for uses like debugging or problem isolation. Consequently, linking different log sources can be difficult, because those log sources may or may not contain common values.

Two log sources could record the same values in different and varied log messages or represent them differently. For example, a log source could format a date as <kbd>MMDDYYYY</kbd>, <kbd>MM-DD-YYYY</kbd>, or <kbd>DD/MM/YYYY</kbd>.

Deciphering dates in various formats may be simple for a human reviewer, but consider the example of a file transfer protocol (FTP) action recorded by one log source as “FTP” and by another as “21,” its well-known port number. Few analysts can easily distinguish the full 1,024 well-known ports by port number.

One approach to dealing with this complexity is to create PERL scripts to search and produce only those log messages matching the query, which is a reasonable approach conceptually, but with the growing complexity and variety of sources, its ability to alleviate the problems of manual log review is limited.

### Archival

Organizations must treat log data like any other data, subject to security and retention policies, as well as compliance mandates. Breach of log data is a serious problem, because those logs often contain sensitive data (such as customer data). As a result, protection of log data—both in transit to the log collection solution and when stored—is an important concern. Therefore, access to log data must be strictly controlled and should never be alterable.

In addition, storing log data centrally from distributed sources across an organization creates a massive storage management challenge. Purchasing and deploying the required storage consumes valuable real estate and power (both for operations and cooling) and must be managed, backed up, and included in disaster-recovery planning.

## Automated log management

As the challenges of log management have grown, so have the benefits of automated log management solutions. An appropriate log management solution provides many benefits to an organization:

* Log collection across all IT infrastructure—on premises, hosted, and in the cloud
* Sophisticated parsing of logs to enable data analysis from a variety of log sources
* Reporting tools that provide insight into your organization’s security posture
* Tools to enable post-incident analysis of log data
* Reliable, regular review of log data that meets compliance mandates as well as security best practices.

The cost of log management tools and services must be weighed against the internal staff time required to attempt log management, as well as the cost of non-compliance, data loss, and security incidents.

* Log management solutions should be evaluated against the practices described in this paper.
* Does the solution provide complete log collection across all sources, in all environments?
* Is log data parsed and normalized to support the required search and analysis functions?
* Is regular log review that meets internal requirements and compliance mandates provided?
* Is data transmitted and stored securely?
* Can data be archived according to organizational retention policies, with appropriate levels of data protection?

## Summary

While compliance initiatives often drive the need for log management, it also provides security- and availability-related benefits as well. Compliance with governing regulations and standards, most-notably PCI DSS 3.1, Sarbanes-Oxley, HIPAA, GLBA, and FISMA, require log collection, retention, and access for forensic analysis.

Benefits from routine log analysis include improved detection of security incidents, policy violations, fraudulent activities, and operational problems. Logs are also useful for establishing performance baselines, performing auditing and forensic analysis, supporting internal investigations and identifying operational trends and long-term problems.