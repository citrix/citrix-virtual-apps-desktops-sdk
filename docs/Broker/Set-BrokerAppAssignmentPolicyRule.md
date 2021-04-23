
# Set-Brokerappassignmentpolicyrule
Modifies an existing application rule in the site's assignment policy.
## Syntax
```
Set-BrokerAppAssignmentPolicyRule [-InputObject] <AppAssignmentPolicyRule[]> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerAppAssignmentPolicyRule [-Name] <String> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerAppAssignmentPolicyRule cmdlet modifies an existing application rule in the site's assignment policy.

An application rule in the assignment policy defines the users who are entitled to a self-service persistent machine assignment from the rule's desktop group; once assigned the machine can run one or more applications published from the group.

Changing an application rule does not alter machine assignments that have already been made by the rule, nor does it affect active sessions to those machines in any way.


## Related Commands

* [New-BrokerAppAssignmentPolicyRule](./New-BrokerAppAssignmentPolicyRule/)
* [Get-BrokerAppAssignmentPolicyRule](./Get-BrokerAppAssignmentPolicyRule/)
* [Rename-BrokerAppAssignmentPolicyRule](./Rename-BrokerAppAssignmentPolicyRule/)
* [Remove-BrokerAppAssignmentPolicyRule](./Remove-BrokerAppAssignmentPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The application rule in the assignment policy to be modified. | true | true (ByValue) |  |
| Name | Specifies the name of the application rule in the assignment policy to be modified. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| AddExcludedUsers | Adds the specified users to the excluded users filter of the application rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from this rule.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| AddIncludedUsers | Adds the specified users to the included users filter of the application rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| Description | Changes the description of the application rule. The text is purely informational for the administrator, it is never visible to the end user. | false | false |  |
| Enabled | Enables or disables the application rule. A disabled rule is ignored when evaluating the site's assignment policy. | false | false |  |
| ExcludedUserFilterEnabled | Enables or disables the excluded users filter. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated. | false | false |  |
| ExcludedUsers | Changes the excluded users filter of the application rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from the rule.<br>This can be used to exclude users or groups who would otherwise gain access by groups specified in the included users filter. | false | false |  |
| IncludedUserFilterEnabled | Enables or disables the included users filter. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a machine assignment by the application rule.<br>Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter. | false | false |  |
| IncludedUsers | Changes the included users filter of the application rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.<br>If a user appears explicitly in the excluded users filter of the rule, or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter. | false | false |  |
| RemoveExcludedUsers | Removes the specified users from the excluded users filter of the application rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from this rule.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| RemoveIncludedUsers | Removes the specified users from the included users filter of the application rule, that is, the users and groups who are granted an entitlement to a machine assignment by the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Appassignmentpolicyrule
The application rule within the assignment policy to be modified.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Appassignmentpolicyrule
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AppAssignmentPolicyRule object.
## Examples

### Example 1
```
C:\PS> Set-BrokerAppAssignmentPolicyRule 'Temp Staff' -AddIncludedUsers office\interns
```
#### Description
Adds the user group OFFICE\\interns to the Temp Staff application rule in the assignment policy. This grants all members of that user group an entitlement to a machine in the rule's desktop group. The machines can run applications published from the group. The application session properties obtained using the rule are determined by the rule's other properties.
### Example 2
```
C:\PS> Set-BrokerAppAssignmentPolicyRule 'Temp Staff' -Enabled $false
```
#### Description
Disables the Temp Staff application rule in the assignment policy. This prevents further machine assignments being made using this rule until it is re-enabled. However, access to machines already assigned using the rule is not impacted.
