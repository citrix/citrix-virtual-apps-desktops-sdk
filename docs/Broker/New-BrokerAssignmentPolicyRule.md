
# New-Brokerassignmentpolicyrule
Creates a new desktop rule in the site's assignment policy.
## Syntax
```
New-BrokerAssignmentPolicyRule [-Name] <String> -DesktopGroupUid <Int32> [-ColorDepth <ColorDepth>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IconUid <Int32>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-MaxDesktops <Int32>] [-PublishedName <String>] [-SecureIcaRequired <Boolean>] [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerAssignmentPolicyRule cmdlet adds a new desktop rule to the site's assignment policy.

A desktop rule in the assignment policy defines the users who are entitled to self-service persistent machine assignments from the rule's desktop group. A rule defines how many machines a user is allowed from the group for delivery of full desktop sessions.

The following constraints apply when creating a desktop assignment rule for a desktop group:


* The group's desktop kind must be Private
* The group's delivery type must be DesktopsOnly
* Only one desktop assignment rule can be created for RemotePC groups.

When a user selects a machine assignment entitlement from a private group, a currently unassigned machine is selected from the group and permanently assigned to the user to create an assigned desktop. A desktop session is then launched to the machine. Subsequent launches are routed directly to the now assigned machine.

Once a machine has been assigned in this way, the original assignment rule plays no further part in access to the new desktop.

Multiple desktop rules in the assignment policy can apply to the same desktop group. Where a user is granted entitlements by more than one rule for the same group, they can have as many machine assignments from the group as the total of their entitlements.


## Related Commands

* [Get-BrokerAssignmentPolicyRule](./Get-BrokerAssignmentPolicyRule/)
* [Set-BrokerAssignmentPolicyRule](./Set-BrokerAssignmentPolicyRule/)
* [Rename-BrokerAssignmentPolicyRule](./Rename-BrokerAssignmentPolicyRule/)
* [Remove-BrokerAssignmentPolicyRule](./Remove-BrokerAssignmentPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the administrative name of the new desktop rule. Each rule in the site's assignment policy must have a unique name (irrespective of whether they are desktop or application rules). | true | true (ByPropertyName) |  |
| DesktopGroupUid | Specifies the unique ID of the desktop group to which the new desktop rule applies. | true | true (ByPropertyName) |  |
| ColorDepth | Specifies the color depth of any desktop sessions to machines assigned by the new rule.<br>Valid values are \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| Description | Specifies an optional description of the new desktop rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| Enabled | Specifies whether the new desktop rule is initially enabled. A disabled rule is ignored when evaluating the site's assignment policy. | false | true (ByPropertyName) | true |
| ExcludedUserFilterEnabled | Specifies whether the excluded users filter is initially enabled. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated. | false | true (ByPropertyName) | false |
| ExcludedUsers | Specifies the excluded users filter of the new desktop rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from the rule.<br>This can be used to exclude users or groups who would otherwise gain access by groups specified in the included users filter. | false | true (ByPropertyName) | (empty list) |
| IconUid | Specifies the unique ID of the icon used to display the machine assignment entitlement to the user, and of the assigned desktop itself following the assignment.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| IncludedUserFilterEnabled | Specifies whether the included users filter is initially enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a machine assignment by the new desktop rule.<br>Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter.<br>For rules that relate to RemotePC desktop groups however, if the included user filter is disabled, the rule is effectively disabled. | false | true (ByPropertyName) | true |
| IncludedUsers | Specifies the included users filter of the new desktop rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.<br>If a user appears explicitly in the excluded users filter of the rule or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter. | false | true (ByPropertyName) | (empty list) |
| MaxDesktops | The number of machines from the rule's desktop group to which a user is entitled. Where an entitlement is granted to a user group rather than an individual, the number of machines applies to each member of the user group independently. | false | true (ByPropertyName) | 1 |
| PublishedName | The name of the new machine assignment entitlement as seen by the user, and of the assigned desktop following its usage.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| SecureIcaRequired | Specifies whether the new desktop rule requires the SecureICA protocol to be used for desktop sessions to machines assigned using the entitlement.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| UUID | An optional GUID for this rule. | false | true (ByPropertyName) | A new GUID is generated if none is supplied. |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Assignmentpolicyrule
New-BrokerAssignmentPolicyRule returns the newly created desktop rule in the assignment policy rule.
## Examples

### Example 1
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'

C:\PS> New-BrokerAssignmentPolicyRule 'UK Office' -DesktopGroupUid $dg.Uid -IncludedUsers sales\uk-staff -PublishedName 'Sales Desktop'
```
#### Description
Creates a desktop rule in the assignment policy that grants all members of the SALES\\uk-staff group an entitlement to a single machine from the Sales Support desktop group. The entitlement name seen by users is Sales Desktop.
