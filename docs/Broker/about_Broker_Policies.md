
# about\_Broker\_Policies

## Topic
Citrix Broker SDK - Access, Entitlement, and Assignment Policies


## Short Description
Overview of the site policies that control users' access to desktop and application sessions.


## Long Description
For an end user to access a desktop or application resource within a site, they must have both an entitlement to use the resource, and have access to the desktop group that contains the resource.

Entitlements to use resources can be granted by one of the following means:


* The site entitlement policy grants entitlements to launch a shared desktop or application session from a pool of shared machines.
* The site assignment policy grants entitlements for "self service" permanent assignment of machines to users for running desktop or application sessions, and is referred to as "Assign On First Use" (AOFU)
* Machines can be permanently assigned ("pre-assigned") to users by the administrator to run either desktop or application sessions.
* Machines can be configured to allow automatic permanent assignment to their normal user (using the RemotePC feature).

A user must also be granted access to the desktop group that contains the resource. These access rights are controlled by the site's access policy.

The access policy controls access using details of the user's device such as whether it's connected over a local area network (LAN) or connected through Access Gateway, the user device's name, IP address or subnet, and the requested connection protocol. The user's identity can also feed into the access check allowing, for example, certain users access to resources only when locally connected to the site, but others full remote access.

Access and entitlements can be combined to allow rich and fine-grained control over which users have access to site resource from any given user device or location.

Each site has a single access policy, entitlement policy, and assignment policy. Each policy comprises a set of rules. Policies are defined by adding, removing, or changing rules.

Each site policy can also be viewed as a set of distinct policies each relating to a single desktop group. In general a group has one or more policy rules that relate to it, however each rule relates to only a single group. Thus the rules that grant entitlement and access rights to a desktop group define the policy for that group and that group only; changing this policy has no impact on the entitlement and access rights for any other other group in the site.

For detailed information about defining policy rules, see: help New-BrokerAccessPolicyRule help New-BrokerEntitlementPolicyRule help New-BrokerAssignmentPolicyRule help New-BrokerAppEntitlementPolicyRule help New-BrokerAppAssignmentPolicyRule

The mapping of policies to the resources that they make available within a site is described briefly below. For specific information on configuring each category of resource, consult the more detailed help topics listed.


### Shared Desktop And Application Sessions
To grant access to a group of shared machines, use the access and entitlement policies:


* The access policy grants access to the desktop group containing the machines to be shared.
* The entitlement policy grants an entitlement to use one or more machines in the group to specified users or groups of users.

Groups of shared machines can be used to deliver full desktop or seamless application sessions, or both.

For more detailed information about configuring shared machines, see: help about\_Broker\_AccessPolicy help about\_Broker\_EntitlementPolicy


### Pre-Assigned Private Machines
To grant access to private machines, use the access policy and a machine assignment:


* The access policy grants access to the desktop group containing the machines.
* The assignment links the desktop to a specified user. You can assign a machine to just one user, multiple users or user groups. However, for single-session machines, only one user can access the machine at a time.

Private machines can be used to deliver full desktop or seamless application sessions (but not both).

For more detailed information about configuring private machines, see: help about\_Broker\_AccessPolicy help Add-BrokerUser


### Assign-On-First-Use (Aofu) Machines
To grant access to a desktop group containing assignable machines, use the access policy and the assignment policy:


* The access policy grants access to the desktop group containing the pool of machines.
* The assignment policy grants users a self-service entitlement to pick one or more machines from the pool.

AOFU machines can be used to deliver full desktop or seamless application sessions (but not both from the same desktop group).

For more detailed information about configuring AOFU desktops, see: help about\_Broker\_AccessPolicy help about\_Broker\_AssignmentPolicy


### Remote Pc Machines
The RemotePC feature allows existing physical machines to be assigned automatically to their normal user thus allowing them remote access to their own machine but without the need for the administrator to individually configure access to each machine.

For more detailed information about configuring the Remote PC feature, see: help about\_Broker\_RemotePC


## See Also

* [about\_Broker\_AccessPolicy](./about_Broker_AccessPolicy/)
* [about\_Broker\_EntitlementPolicy](./about_Broker_EntitlementPolicy/)
* [about\_Broker\_AssignmentPolicy](./about_Broker_AssignmentPolicy/)
* [about\_Broker\_RemotePC](./about_Broker_RemotePC/)
* [New-BrokerAccessPolicyRule](./New-BrokerAccessPolicyRule/)
* [New-BrokerEntitlementPolicyRule](./New-BrokerEntitlementPolicyRule/)
* [New-BrokerAssignmentPolicyRule](./New-BrokerAssignmentPolicyRule/)
* [New-BrokerAppEntitlementPolicyRule](./New-BrokerAppEntitlementPolicyRule/)
* [New-BrokerAppAssignmentPolicyRule](./New-BrokerAppAssignmentPolicyRule/)
* [Add-BrokerUser](./Add-BrokerUser/)

