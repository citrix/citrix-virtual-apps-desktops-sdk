
# about\_Broker\_AssignmentPolicy

## Topic
Citrix Broker SDK - Assignment Policy


## Short Description
Controls the automatic, permanent assignment of machines to users.


## Long Description
The site's assignment policy defines rules controlling automatic assignment of machines to users in a process referred to as Assign On First Use (AOFU).

In this assignment model, a desktop group is initially populated with machines that have no assignments, and users are granted entitlements to obtain a machine selected at random from the pool by self-service assignment. Once made, the assignment is permanent. The resulting assigned machines can be used to deliver either desktop or application sessions depending on the delivery type of the desktop group.

The assignment policy comprises a set of rules. The policy can be applied only to desktop groups of desktop kind Private.

For assignment of machines to deliver desktop sessions:


* Multiple rules can apply to the same desktop group.
* Each rule grants an entitlement to one or more machines.

For assignment of machines to deliver application sessions:


* Only a single rule can apply to a given desktop group.
* Each rule grants an entitlement to a single machine.
* Although only a single application assignment rule can be defined for a group, a user can still launch multiple applications from that group because the applications all run within the same session on the assigned machine.

Once a machine is assigned to a user by an assignment policy rule, the rule plays no further part in controlling access to that machine. The rule can be changed, or even removed, without impacting the user's access to the machine.

Rules for desktop and application machine assignments are distinct. Desktop assignments are managed through the BrokerAssignmentPolicyRule SDK object, and application rules through the BrokerAppAssignmentPolicyRule object.

Desktop machine assignment rules can  be created only for desktop groups with delivery type DesktopsOnly, whereas an application machine assignment rule can be created only for delivery type AppsOnly.

Because desktop groups of assigned machines do not allow delivery type DesktopsAndApps, desktop machine assignment and application machine assignment rules cannot exist for the same desktop group.

Assignment policy rules are also used to configure the RemotePC feature where their detailed usage differs. For more information on the RemotePC feature see "help about\_Broker\_RemotePC".

For an entitlement granted by the assignment policy to be available to a user, the site's access policy must also grant them access to the desktop group.


## Assignment Policy Rules
Each assignment policy rule has the following key properties:


* The desktop group to which it applies (one rule only ever applies to one group).
* The users to which machines can be assigned by the rule.

Additionally for desktop assignment rules, the following properties exist:


* The published name of the entitlement (visible to the user).
* The number of machines (entitlements) to which the rule grants access.
* The properties that a newly assigned desktop acquires.

If multiple desktop assignment rules entitle a user to machines from the same desktop group, their total machine entitlement is the sum of those granted by all those rules. The properties of the desktop sessions obtained may differ depending on which of the entitlements the user selects to start a session.

Each rule can be individually enabled or disabled. A disabled rule is ignored when the assignment policy is evaluated.


### User Filters (Full)
Each rule has two user filters, an include filter and an exclude filter:


* The include filter contains users and user groups that are granted entitlements to machines.
* The exclude filter contains users and user groups that are denied entitlements to machines.

If the include filter of a rule contains multiple instances of a user (either explicit or implicit), this does not alter the number of machine entitlements granted to them by the rule.

Entries in the exclude filter take priority, so if a user appears explicitly or implicitly in both filters, access is denied. Typically, you use this filter to exclude a user or group of users who would otherwise gain access because they are members of a user group specified in the include filter.

Because all rules are independently evaluated, the exclude filter can exclude only users who would otherwise gain an entitlement through the same rule's include filter. That is, if a user is in a rule's include filter but not its exclude filter, the rule is guaranteed to grant that user access to a machine irrespective of whether the user appears in the exclude filter of other rules.

If a filter contains a user group that contains other users and groups, the filter implicitly includes all of those users and groups.

By default the exclude filter is disabled.

To maintain assignment policy rules that can be fully displayed and edited with Citrix Studio, use the simplified user filter model below and do not use the exclude filter.


### User Filters (Simplified)
The included user filter described above also supports a simplified usage model where the filter itself is disabled. When this is done, any user who has access to the desktop group through the access policy is implicitly granted an entitlement to a machine through the entitlement policy rule without the need to list the user in the rule's include filter.

This is useful in cases where the access policy for the desktop group already explicitly specifies the users who should have access.

Even if the include filter is disabled, the exclude filter can still be used to deny the entitlement to users who would otherwise gain access through the access policy alone.

This simplified usage cannot be used for RemotePC desktop groups.


### Remote Pc Usage
When a desktop group is configured as a RemotePC group, the usage of the assignment policy differs in the following ways:


* Only a single rule can apply to a given desktop group.
* The delivery type of the desktop group must be DesktopsOnly.
* The simplified user filter model cannot be used. Users or user groups must appear explicitly in the included user filter of the assignment policy rule.
* If the included user filter is disabled then RemotePC assignment for the group is also effectively disabled.

For more information on the RemotePC feature see "help about\_Broker\_RemotePC".


## Additional Desktop Assignment Rule Properties
Desktop assignment rules specify the following additional properties:


* PublishedName
* Description
* IconUid
* ColorDepth
* SecureIcaRequired

The published name, description, and icon UID properties apply to the desktop entitlement itself and determine the way in which the entitlement is presented to the user in, for example, StoreFront.

The color depth and secure ICA properties apply to the desktop session that is obtained when the entitlement is used.

In all cases, these properties can be explicitly specified. However, a null value (the default) means that the corresponding property is taken from the desktop group to which the rule applies. This inheritance from groups is dynamic; if the property of the group changes, the property of the entitlement changes too.

For assignment rules these properties are copied to the newly assigned desktop when the granted entitlement is first used. If the properties on the rule are subsequently changed the properties on the user's assigned desktop do not change. The dynamic inheritance of desktop properties from the desktop group continues after the assignment has occurred if the original rule did not provide explicit property values.


## Calculating Overall Machine Entitlements
Assignment rules are modified only by the SDK; they are not modified when used by the system to make automatic assignments. The number of machine entitlements offered to the user is determined by the number of machines (within the desktop group) already assigned to them and by which rules those assignments were made.

For each desktop group, the number of desktop entitlements available to the user is determined as follows:


1.   The total number of entitlements for the user to machines in the group, from all rules, is calculated.
2.   The total number of assigned machines (from any source) that the user already has in the group is determined.
3.   The outstanding entitlement value is derived as the difference of the above two numbers.
4.   If the outstanding entitlement value is zero or fewer, no further entitlements are allowed. Otherwise, for each applicable rule, the number of entitlements is that defined by the rule itself, minus the number of desktops already assigned to the user by that rule, and capped by the outstanding entitlement value.

Desktop and application machine entitlements both follow the above rules. However, because only a single application assignment rule granting a single entitlement per group can exist, these rules are seldom a consideration for applications.


### Examples
Simple case: A user is entitled to a single machine in a group by a single assignment rule:


  1.   On first use, the user sees a single desktop entitlement. If the user selects this, a new desktop is assigned.
  2.   On subsequent uses, the user sees the assigned desktop only. No other entitlements are displayed.

Complex case: A user is entitled to two machines, one from each of two different rules, A and B, both applying to the same desktop group. In addition, the user has a machine explicitly assigned to them by the administrator within that group:


  1.   On first use, the user sees the administrator-assigned desktop, a single entitlement to a desktop of type A, and a single entitlement to a desktop of type B. If either of the entitlements is selected, a desktop of the appropriate type, A or B, is assigned.
  2.   On subsequent uses, the user sees the administrator-assigned desktop and the desktop assigned by the selected entitlement. No further entitlements are displayed.

### Machine Entitlement Presentation

For desktop machine assignment rules, the user interface determines whether users can visually distinguish between an entitlement to a machine and an actual assigned desktop. This cannot be controlled by Broker SDK cmdlets.

Although the number of entitlements seen by users takes account of all of their currently assigned desktops, the dynamic state of the system can affect the user interaction. This means that entitlements are displayed even where the pool of machines is empty, or the remaining desktops are in maintenance mode or otherwise unavailable. If the user attempts to use an entitlement in these cases, they receive a no-available-desktop error.

For application machine entitlement rules, the entitlements themselves are not presented to the end user; only the applications available to the user are presented. The use of available assignments, or of already assigned machines, is managed automatically.


## Notes
If an assignment rule grants entitlements to a user group:


* The machine is assigned to the user who selects the entitlement, thus an assignment policy rule cannot be used to assign a machine to a user group. However, an administrator can assign a machine to a user group using the Add-BrokerUser cmdlet.
* The number of machine entitlements specified in a desktop assignment rule applies to each member of the user group. For example, if a rule grants a user group access to two machines, every user in the group is entitled to two desktops.

The total number of machine entitlements defined by the assignment policy for a given desktop group may exceed the number of machines present in the group. A user attempting to use an entitlement when the pool of machines is empty receives a no-desktop-available error. (See CALCULATING OVERALL MACHINE ENTITLEMENTS above).

A machine assigned to a user as a result of the assignment policy remains permanently assigned unless the machine assignment itself is removed by the administrator. Such assignments are permanent even if the assignment rule is deleted, when the machine is treated as administrator-assigned.

The assignment policy cannot be used to assign a machine to more than one user. This is only possible using the Add-BrokerUser cmdlet.


## See Also

* [about\_Broker\_Policies](./about_Broker_Policies/)
* [about\_Broker\_AccessPolicy](./about_Broker_AccessPolicy/)
* [about\_Broker\_EntitlementPolicy](./about_Broker_EntitlementPolicy/)
* [about\_Broker\_Applications](./about_Broker_Applications/)
* [New-BrokerAssignmentPolicyRule](./New-BrokerAssignmentPolicyRule/)
* [Get-BrokerAssignmentPolicyRule](./Get-BrokerAssignmentPolicyRule/)
* [Set-BrokerAssignmentPolicyRule](./Set-BrokerAssignmentPolicyRule/)
* [Rename-BrokerAssignmentPolicyRule](./Rename-BrokerAssignmentPolicyRule/)
* [Remove-BrokerAssignmentPolicyRule](./Remove-BrokerAssignmentPolicyRule/)
* [New-BrokerAppAssignmentPolicyRule](./New-BrokerAppAssignmentPolicyRule/)
* [Get-BrokerAppAssignmentPolicyRule](./Get-BrokerAppAssignmentPolicyRule/)
* [Set-BrokerAppAssignmentPolicyRule](./Set-BrokerAppAssignmentPolicyRule/)
* [Rename-BrokerAppAssignmentPolicyRule](./Rename-BrokerAppAssignmentPolicyRule/)
* [Remove-BrokerAppAssignmentPolicyRule](./Remove-BrokerAppAssignmentPolicyRule/)
* [Add-BrokerUser](./Add-BrokerUser/)

