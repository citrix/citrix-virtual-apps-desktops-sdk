
# Set-Brokerassignmentpolicyrule
Modifies an existing desktop rule in the site's assignment policy.
## Syntax
```
Set-BrokerAssignmentPolicyRule [-InputObject] <AssignmentPolicyRule[]> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-ColorDepth <ColorDepth>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IconUid <Int32>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-MaxDesktops <Int32>] [-PublishedName <String>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-SecureIcaRequired <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerAssignmentPolicyRule [-Name] <String> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-ColorDepth <ColorDepth>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IconUid <Int32>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-MaxDesktops <Int32>] [-PublishedName <String>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-SecureIcaRequired <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerAssignmentPolicyRule cmdlet modifies an existing desktop rule in the site's assignment policy.

A desktop rule in the assignment policy defines the users who are entitled to self-service persistent machine assignments from the rule's desktop group. A rule defines how many machines a user is allowed from the group for delivery of full desktop sessions.

Changing a desktop rule does not alter machine assignments that have already been made by the rule, nor does it affect active sessions to those machines in any way.


## Related Commands

* [New-BrokerAssignmentPolicyRule](./New-BrokerAssignmentPolicyRule/)
* [Get-BrokerAssignmentPolicyRule](./Get-BrokerAssignmentPolicyRule/)
* [Rename-BrokerAssignmentPolicyRule](./Rename-BrokerAssignmentPolicyRule/)
* [Remove-BrokerAssignmentPolicyRule](./Remove-BrokerAssignmentPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The desktop rule in the assignment policy to be modified. | true | true (ByValue) |  |
| Name | Specifies the name of the desktop rule in the assignment policy to be modified. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| AddExcludedUsers | Adds the specified users to the excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from this rule.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| AddIncludedUsers | Adds the specified users to the included users filter of the rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| ColorDepth | Changes the color depth of any desktop sessions to machines assigned by the rule.<br>Valid values are \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| Description | Changes the description of the desktop rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.<br>A null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| Enabled | Enables or disables the desktop rule. A disabled rule is ignored when evaluating the site's assignment policy. | false | false |  |
| ExcludedUserFilterEnabled | Enables or disables the excluded users filter. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated. | false | false |  |
| ExcludedUsers | Changes the excluded users filter of the desktop rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from this rule.<br>This can be used to exclude users or groups who would otherwise gain access by groups specified in the included users filter. | false | false |  |
| IconUid | Changes the unique ID of the icon used to display the machine assignment entitlement to the user, and of the assigned desktop itself following the assignment.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| IncludedUserFilterEnabled | Enables or disables the included users filter. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a machine assignment by the rule.<br>Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter.<br>For rules that relate to RemotePC desktop groups however, if the included user filter is disabled, the rule is effectively disabled. | false | false |  |
| IncludedUsers | Changes the included users filter of the rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.<br>If a user appears explicitly in the excluded users filter of the rule, or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter. | false | false |  |
| MaxDesktops | The number of machines from the rule's desktop group to which a user is entitled. Where an entitlement is granted to a user group rather than an individual, the number of machines applies to each member of the user group independently. | false | false |  |
| PublishedName | Changes the published name of the machine assignment entitlement as seen by the user. Changing the published name does not affect the names of desktops that have already been assigned by the rule.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| RemoveExcludedUsers | Removes the specified users from the excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from this rule.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| RemoveIncludedUsers | Removes the specified users from the included users filter of the desktop rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| SecureIcaRequired | Changes whether the desktop rule requires the SecureICA protocol for desktop sessions to machines assigned using the entitlement.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Assignmentpolicyrule
The desktop rule within the assignment policy to be modified.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Assignmentpolicyrule
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AssignmentPolicyRule object.
## Examples

### Example 1
```
C:\PS> Set-BrokerAssignmentPolicyRule 'Temp Staff' -AddIncludedUsers office\interns
```
#### Description
Adds the user group OFFICE\\interns to the Temp Staff desktop rule in the assignment policy. This grants all members of that user group entitlements to machines in the rule's desktop group. The number of machine entitlements per user and the session properties of the desktops obtained using the rule are determined by the rule's other properties.
### Example 2
```
C:\PS> Set-BrokerAssignmentPolicyRule 'Temp Staff' -Enabled $false
```
#### Description
Disables the Temp Staff desktop rule in the assignment policy. This prevents further machine assignments being made using this rule until it is re-enabled. However, access to machines already assigned using the rule is not impacted.
