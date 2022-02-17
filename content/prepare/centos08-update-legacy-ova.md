# CentOS Version 8 Update for  Legacy Customers using OVA

CentOS announced the end of life for their version 6 operating system. This means CentOS will no longer provide security patches, vulnerabilities, or bug fixes for version 6. As a result, Alert Logic is helping customers update all Alert Logic appliances running on operating system CentOS version 6 to the current and supported version 8.

As Alert Logic transitions all customers to CentOS 8, Alert Logic will continue maintain necessary security updates for CentOS version 6 to ensure all customers remain secure.

## How to update for legacy customers using OVA image

You must first install and claim the new appliance, ensure the assignment policy is in the new appliance, terminate the old appliance, and then remove the assignment policy from it. After you verify that the agent  is sending data to the new appliance, you must request Alert Logic to decommission the old appliance.

1. You must install a new appliance for every appliance you are currently running with					the new OVA image. See [Install and Configure the Virtual Appliance](virtual-appliance.md)
2. After the new appliance or appliances are claim spun up, verify that the  assignment policy has the new appliance(s) in it. If you do not see the  assignment policy, you must add the appliance(s) to the current assignment policy that is in use with the default assignment policy for the agent. To create an assignment policy, see the [Create an assignment policy](https://legacy.docs.alertlogic.com/install/cloud/amazon-web-services-threat-manager-direct-linux.htm#Createanassignmentpolicy) section.
3. After the old appliance is terminated, verify the agent is sending data to the new appliance. To verify in the Alert Logic console:
Statistics are updated every 15 minutes in the Alert Logic console.
   1. Click the **Configuration** tab.
   2. Click **All Deployments**.
   3. Click **Networks and Protected Hosts**, and then click the **Protected Hosts** tab.
   4. Click on the agent to see more details.
5. After the assignment policy has the new appliance, you can terminate the old appliance and remove it from the assignment policy. The agents will automatically shift over to the new appliance(s). To learn how to manage assignment policies, see the [Delete an assignment policy](https://legacy.docs.alertlogic.com/userGuides/threat-manager-policies.htm#Deleteanassignmentpolicy) section.
6. After you have confirmed the new appliance is running, the assignment policy has the new appliance and the old appliance is terminated, you can submit a ticket to [Alert LogicTechnical Support](mailto:support@alertlogic.com) with the  ID of the old appliance for them to decommission.

## How to update other products

If you are not running an Ova image for your legacy deployments, refer to the links below for specific instructions depending on your subscription and services:

* MDR** customers with **AWS** deployments**: See [CentOS Version 8 Update for AWS MDR Customers](centos08-update-mdr-aws.md) for more details.
* MDR** customers using an OVA image**: See [CentOS Version 8 Update for  Legacy Customers using OVA](#) for more details.
* Cloud Defender** or other legacy products customers with **AWS** deployments**: See [CentOS Version 8 Update for AWS Legacy Customers](centos08-update-legacy-aws.md) for more details.
* Alert Logic Managed Web Application Firewall (WAF)** subscription**: Alert Logic has already contacted you, or will contact you soon, to coordinate a time to update your appliance.
* Threat Manager** subscription**: Alert Logic will contact you soon on the process and details for this transition.

OVA ESXi 6.5 is the lowest supported version, and you will not be able to update to CentOS 8 if you are using an older version.