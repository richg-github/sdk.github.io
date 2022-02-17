# About Alert Logic Deployment Types

A deployment allows you to monitor and protect a defined set of assets from your appliances, agents, hosts, and collectors from your environments. You can create deployments for assets found in your Amazon Web Services (AWS) and Microsoft Azure cloud platforms, and from other cloud-based or physical Data Centers.

Alert Logic discovers and organizes deployments into a visual topology where you can select the desired levels of protection for your assets. You must choose one of the following levels of coverage for each asset:

* Unprotected
* Alert Logic Essentials coverage
* Alert Logic Professional coverage

## Coverage protection levels

### Alert Logic Essentials

Alert Logic MDR Essentials coverage provides deployment automation for assets in your AWS or Azure environments, access to continuous asset discovery, and asset visibility for your deployments. Alert Logic continuously tests your environments with vulnerability scanning and cloud configuration scanning to help you detect and remediate exposures.

### Alert Logic Professional

Alert Logic MDR Professional coverage provides the capabilities from Essentials, plus access to network intrusion detection, and log and security analytics.

## Deployment types

### AWS Deployments

Alert Logic supports integrations with several AWS security services. To protect your AWS deployment, you must set up an AWS cross-account role to allow Alert Logic access to your AWS account. The Alert Logic console steps you through IAM role creation.

To protect your AWS deployment, you must set up an AWS IAM role and policy to allow Alert Logic access to your AWS account. Alert Logic provides AWS CloudFormation templates to automate creation of the correct policy and role for the deployment mode you choose. The deployment mode you choose determines how Alert Logic deploys your scanning instances. You can also choose to employ manual setup in which you log into the AWS console and create your IAM policy and role.

Each deployment mode allows a different level of control over the creation of scanning instances and subnets.

### Automatic Mode

Alert Logic recommends  Automatic Mode  if you want Alert Logic to deploy and maintain new VPC subnets used for scanning instances. If you choose Automatic Mode, you can create the IAM policy and role using either an AWS CloudFormation template or your own policy document.

If you create a deployment with Automatic Mode, Alert Logic creates the following:

* A CloudTrail log source if one is not present
* A new Outcomes SQS Queue
* An SNS Topic if one is not available and linked to the CloudTrail log source.

In addition, after discovery and initial setup takes place, you must choose your subscription level to determine asset deployments.

For an Essentials subscription, Alert Logic automatically deploys the following:

* A single /28 subnet per scoped VPC with required routing to the internet (Internet gateway and routing table setup)
* A single scanning EC2 instance (c5.xlarge by default)

For Professional and Enterprise subscriptions, Alert Logic automatically deploys the following:

* Two /28 subnets per scoped VPC with required routing to the internet (Internet gateway and routing table setup)
* A single scanning EC2 instance (c5.xlarge by default)
* One IDS per Availability Zone (c5.xlarge by default)

For information about creating a deployment using Automatic Mode, see [Amazon Web Services (AWS) Deployment Configuration—Automatic Mode](aws-auto.md).

### Manual Mode

Select Manual Mode if you want to manage subnets for scanning instances when you create an AWS deployment. If you choose Manual Mode, you can create the IAM policy and role using either an AWS CloudFormation template or your own policy document.

For information about creating a deployment using Manual Mode, see [Amazon Web Services (AWS) Deployment Configuration—Manual Mode](aws-manual.md).

### Azure Deployments

Alert Logic supports integration with several Azure services. To protect your Azure deployment, you must create an Role-Based Access Control (RBAC) role in Azure to allow Alert Logic to access your account.

For information about Azure deployment configuration, see [Microsoft Azure Deployment Configuration](azure.md).

### Data Center Deployments

The Data Center environments are deployments you manually configure. The Data Center page displays the list of appliances, agents, hosts, and log collectors if subscribed to the Professional  coverage.

For more information on Data Center deployment configuration, see [Data Center Deployment Configuration (Essentials Subscription)](../data-center-essentials.md).

## Deployment Creation Overview

After you click the add  icon (![](../../Resources/Images/Icons/cdAddPlus.png)) and select the deployment type you want to add, the Alert Logic console prompts you through the following steps:

1. Configure   third-party access to cloud-based assets (AWS and Azure deployments only)
2. Discover assets
3. Add assets
4. Define the scope of your protection
5. Schedule scans
6. Install agents or appliances
7. Set up log sources

### Provide Alert Logic third-party access

When you create an AWS or Azure deployment, you must grant Alert Logic access to your cloud environments for asset discovery and scanning. The access granted Alert Logic provides only the amount of access required to monitor the assets in your cloud environments.

### Assets discovery

After you grant Alert Logic access  to your cloud account or subscription, Alert Logic automatically discovers its assets. Alert Logic displays the assets discovered in your account in a visual topology diagram. To learn more about topology, see [Topology](../../analyze/topology.md).

If Alert Logic does not discover all your assets, you can add external assets by domain name or IP address.

### Add assets

For Data Center deployments, you must manually add assets by network, subnet, domain name, or IP address.

### Define your scope of protection

You can define the scope of your protection per network basis. Each network appears within its protected region. Click a region or individual network to set the scan level or leave it unprotected. You also have the option to exclude assets or tags from external scanning, internal scanning, and Network IDS.

### Scheduling scans

Alert Logic automatically performs certain scans. You can schedule when and how often you want Alert Logic to scan for new assets or perform vulnerability scans.

### Configuration topology overview

This topology diagram provides an overview of your scope of protection. You can see which assets are unprotected, or are scanned at the Essentials or Professional levels.

### Installing agents or appliances

**Agents**

Alert Logic provides a single agent that collects data used for analysis, such as log messages and network traffic, metadata, and host identification information. For more information about installing agent installations, see [Install the Alert Logic Agent for Linux](../../prepare/alert-logic-agent-linux.md) or [Install the Alert Logic Agent for Windows](../../prepare/alert-logic-agent-windows.md).

Appliances

If you are configuring a Data Center deployment, you must assign appliances to your networks. Use the Unique Registration Key to assign one or more appliances to each network. For more information about installing a physical appliance or a virtual appliance, see [Install and Configure the  Virtual Appliance](../../prepare/virtual-appliance.md) or [Install and Configure the  Physical Appliance](../../prepare/alert-logic-physical-appliance.md).

### Set up log sources

If you have a Professional subscription, you can set up log collection. To add log sources for data you want to collect, see [Log Sources](../log-sources.md#top).