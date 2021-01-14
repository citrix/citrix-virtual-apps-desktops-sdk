
# Set-Brokerappentitlementpolicyrule
Modifies an existing application rule in the site's entitlement policy.
## Syntax
```
Set-BrokerAppEntitlementPolicyRule [-InputObject] <AppEntitlementPolicyRule[]> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LeasingBehavior <LeasingBehavior>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-SessionReconnection <SessionReconnection>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerAppEntitlementPolicyRule [-Name] <String> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LeasingBehavior <LeasingBehavior>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-SessionReconnection <SessionReconnection>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerAppEntitlementPolicyRule cmdlet modifies an existing application rule in the site's entitlement policy.

An application rule in the entitlement policy defines the users who are allowed per-session access to a machine to run one or more applications published from the rule's desktop group.

Changing a rule does not affect existing sessions launched using the rule, but if the change removes an entitlement to a machine that was previously granted, users may be unable to reconnect to a disconnected session on that machine.


## Related Commands

* [New-BrokerAppEntitlementPolicyRule](./New-BrokerAppEntitlementPolicyRule/)
* [Get-BrokerAppEntitlementPolicyRule](./Get-BrokerAppEntitlementPolicyRule/)
* [Rename-BrokerAppEntitlementPolicyRule](./Rename-BrokerAppEntitlementPolicyRule/)
* [Remove-BrokerAppEntitlementPolicyRule](./Remove-BrokerAppEntitlementPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The application rule in the entitlement policy to be modified. | true | true (ByValue) |  |
| Name | The name of the application rule in the entitlement policy to be modified. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| AddExcludedUsers | Adds the specified users to the excluded users filter of the rule, that is, the users and groups who are explicitly denied entitlements to run applications published from the desktop group.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| AddIncludedUsers | Adds the specified users to the included users filter of the rule, that is, the users and groups who are granted an entitlement to an application session by the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| Description | Changes the description of the application rule. The text is purely informational for the administrator, it is never visible to the end user. | false | false |  |
| Enabled | Enables or disables the application rule. A disabled rule is ignored when evaluating the site's entitlement policy. | false | false |  |
| ExcludedUserFilterEnabled | Enables or disables the excluded users filter. If the filter is disabled then any user entries in the filter are ignored when entitlement policy rules are evaluated. | false | false |  |
| ExcludedUsers | Changes the excluded users filter of the rule, that is, the users and groups who are explicitly denied entitlements to run applications published from the desktop group.<br>This can be used to exclude users or groups or users who would otherwise gain access by groups specified in the included users filter. | false | false |  |
| IncludedUserFilterEnabled | Enables or disables the included users filter. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to an application session by the application rule.<br>Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter. | false | false |  |
| IncludedUsers | Changes the included users filter of the rule, that is, the users and groups who are granted an entitlement to an application session by the rule.<br>If a user appears explicitly in the excluded users filter of the rule or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter. | false | false |  |
| LeasingBehavior | Defines the desired connection leasing behavior applied to sessions launched using this entitlement. Possible values are:<br>Allowed and Disallowed.<br>The Allowed value indicates that connection leasing should behave normally. The Disallowed value prevents users from launching or reconnecting to sessions using this entitlement while connection leasing is active (typically during a database outage). | false | false |  |
| RemoveExcludedUsers | Removes the specified users from the excluded users filter of the application rule, that is, the users and groups who are explicitly denied entitlements to run applications published from the desktop group.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| RemoveIncludedUsers | Removes the specified users from the included users filter of the rule, that is, the users and groups who are granted an entitlement to an application session by the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| SessionReconnection | Defines reconnection (roaming) behavior for sessions launched using this rule. Possible values are:<br>Always, DisconnectedOnly, and SameEndpointOnly. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Appentitlementpolicyrule
The application rule in the entitlement policy rule to be modified.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Appentitlementpolicyrule
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AppEntitlementPolicyRule object.
## Examples

### Example 1
```
C:\PS> Set-BrokerAppEntitlementPolicyRule 'Temp Workers' -AddIncludedUsers office\contractors
```
#### Description
Adds the user group OFFICE\\contractors to those entitled to run applications from the rule's associated desktop group. This grants all members of that group an entitlement to an application session from that group.
### Example 2
```
C:\PS> Set-BrokerAppEntitlementPolicyRule 'Temp Workers' -Enabled $false
```
#### Description
Disables the Temp Workers application rule in the entitlement policy. This prevents further application sessions being launched using this rule until it is re-enabled. However, access to existing application sessions is not affected.
