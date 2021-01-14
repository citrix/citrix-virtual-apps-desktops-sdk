
# New-Brokerappassignmentpolicyrule
Creates a new application rule in the site's assignment policy.
## Syntax
```
New-BrokerAppAssignmentPolicyRule [-Name] <String> -DesktopGroupUid <Int32> [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerAppAssignmentPolicyRule cmdlet adds a new application rule to the site's assignment policy.

An application rule in the assignment policy defines the users who are entitled to a self-service persistent machine assignment from the rule's desktop group; once assigned the machine can run one or more applications published from the group.

The following constraints apply when creating an application assignment rule for a desktop group:


* The group's desktop kind must be Private
* The group's delivery type must be AppsOnly
* Only a single application rule can apply to a given group
* Application assignment rules cannot be applied to RemotePC groups.

When a user selects an application published from a private group, a currently unassigned machine is selected from the group and permanently assigned to the user. An application session is then launched to the machine. Subsequent launches are routed directly to the now assigned machine.

Once a machine has been assigned in this way, the original assignment rule plays no further part in access to the machine.


## Related Commands

* [Get-BrokerAppAssignmentPolicyRule](./Get-BrokerAppAssignmentPolicyRule/)
* [Set-BrokerAppAssignmentPolicyRule](./Set-BrokerAppAssignmentPolicyRule/)
* [Rename-BrokerAppAssignmentPolicyRule](./Rename-BrokerAppAssignmentPolicyRule/)
* [Remove-BrokerAppAssignmentPolicyRule](./Remove-BrokerAppAssignmentPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the administrative name of the new application rule. Each rule in the site's assignment policy must have a unique name (irrespective of whether they are desktop or application rules). | true | true (ByPropertyName) |  |
| DesktopGroupUid | Specifies the unique ID of the desktop group to which the new application rule applies. | true | true (ByPropertyName) |  |
| Description | Specifies an optional description of the new application rule. The text is purely informational for the administrator, it is never visible to the end user. | false | true (ByPropertyName) | null |
| Enabled | Specifies whether the new application rule is initially enabled. A disabled rule is ignored when evaluating the site's assignment policy. | false | true (ByPropertyName) | true |
| ExcludedUserFilterEnabled | Specifies whether the excluded users filter is initially enabled. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated. | false | true (ByPropertyName) | false |
| ExcludedUsers | Specifies the excluded users filter of the new application rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from the rule.<br>This can be used to exclude users or groups who would otherwise gain access by groups specified in the included users filter. | false | true (ByPropertyName) | (empty list) |
| IncludedUserFilterEnabled | Specifies whether the included users filter is initially enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a machine assignment by the new application rule.<br>Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter. | false | true (ByPropertyName) | true |
| IncludedUsers | Specifies the included users filter of the new application rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.<br>If a user appears explicitly in the excluded users filter of the rule or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter. | false | true (ByPropertyName) | (empty list) |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Appassignmentpolicyrule
New-BrokerAppAssignmentPolicyRule returns the newly created application rule in the assignment policy.
## Examples

### Example 1
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'

C:\PS> New-BrokerAppAssignmentPolicyRule 'UK Office' -DesktopGroupUid $dg.Uid -IncludedUsers sales\uk-staff
```
#### Description
Creates an application rule in the assignment policy that grants all members of the SALES\\uk-staff group an entitlement to a single machine from the Sales Support desktop group. The machine can be used for running applications published from the group.
