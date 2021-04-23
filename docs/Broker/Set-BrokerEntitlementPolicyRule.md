
# Set-Brokerentitlementpolicyrule
Modifies an existing desktop rule in the site's entitlement policy.
## Syntax
```
Set-BrokerEntitlementPolicyRule [-InputObject] <EntitlementPolicyRule[]> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-ColorDepth <ColorDepth>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IconUid <Int32>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LeasingBehavior <LeasingBehavior>] [-MaxPerEntitlementInstances <Int32>] [-PublishedName <String>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-RestrictToTag <String>] [-SecureIcaRequired <Boolean>] [-SessionReconnection <SessionReconnection>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerEntitlementPolicyRule [-Name] <String> [-PassThru] [-AddExcludedUsers <User[]>] [-AddIncludedUsers <User[]>] [-ColorDepth <ColorDepth>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IconUid <Int32>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LeasingBehavior <LeasingBehavior>] [-MaxPerEntitlementInstances <Int32>] [-PublishedName <String>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedUsers <User[]>] [-RestrictToTag <String>] [-SecureIcaRequired <Boolean>] [-SessionReconnection <SessionReconnection>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerEntitlementPolicyRule cmdlet modifies an existing desktop rule in the site's entitlement policy.

A desktop rule in the entitlement policy defines the users who are allowed per-session access to a machine from the rule's associated desktop group to run a full desktop session.

Changing a rule does not affect existing sessions launched using the rule, but if the change removes an entitlement to a machine that was previously granted, users may be unable to reconnect to a disconnected session on that machine.


## Related Commands

* [New-BrokerEntitlementPolicyRule](./New-BrokerEntitlementPolicyRule/)
* [Get-BrokerEntitlementPolicyRule](./Get-BrokerEntitlementPolicyRule/)
* [Rename-BrokerEntitlementPolicyRule](./Rename-BrokerEntitlementPolicyRule/)
* [Remove-BrokerEntitlementPolicyRule](./Remove-BrokerEntitlementPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The desktop rule in the entitlement policy to be modified. | true | true (ByValue) |  |
| Name | The name of the desktop rule in the entitlement policy to be modified. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| AddExcludedUsers | Adds the specified users to the excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a desktop session from this rule.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| AddIncludedUsers | Adds the specified users to the included users filter of the rule, that is, the users and groups who are granted an entitlement to a desktop session by the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| ColorDepth | Changes the color depth of any desktop sessions launched by a user from this entitlement. Existing sessions are not affected.<br>Valid values are \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit.<br>A null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| Description | Changes the description of the desktop rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.<br>A null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| Enabled | Enables or disables the desktop rule. A disabled rule is ignored when evaluating the site's entitlement policy. | false | false |  |
| ExcludedUserFilterEnabled | Enables or disables the excluded users filter. If the filter is disabled then any user entries in the filter are ignored when entitlement policy rules are evaluated. | false | false |  |
| ExcludedUsers | Changes the excluded users filter of the desktop rule, that is, the users and groups who are explicitly denied an entitlement to a desktop session from this rule.<br>This can be used to exclude users or groups who would otherwise gain access by groups specified in the included users filter. | false | false |  |
| IconUid | Changes the icon (identified by its unique ID) for the published desktop entitlement as seen by the user.<br>A null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| IncludedUserFilterEnabled | Enables or disables the included users filter. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a desktop session by the rule.<br>Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter. | false | false |  |
| IncludedUsers | Changes the included users filter of the desktop rule, that is, the users and groups who are granted an entitlement to a desktop session by the rule.<br>If a user appears explicitly in the excluded users filter of the rule or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter. | false | false |  |
| LeasingBehavior | Defines the desired connection leasing behavior applied to sessions launched using this entitlement. Possible values are:<br>Allowed and Disallowed.<br>The Allowed value indicates that connection leasing should behave normally. The Disallowed value prevents users from launching or reconnecting to sessions using this entitlement while connection leasing is active (typically during a database outage). | false | false |  |
| MaxPerEntitlementInstances | Maximum allowed concurrently running instances of the desktop associated with this entitlement in the site . A value of zero allows unlimited usage. | false | false |  |
| PublishedName | Changes the name of the published desktop entitlement as seen by the user.<br>A null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| RemoveExcludedUsers | Removes the specified users from the excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a desktop session from this rule.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| RemoveIncludedUsers | Removes the specified users from the included users filter of the desktop rule, that is, the users and groups who are granted an entitlement to a desktop session by the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| RestrictToTag | Optional tag that may be used further to restrict which machines may be made accessible to a user by an entitlement policy rule. A machine may be made accessible by an entitlement policy rule only if either the rule has no tag restriction or the rule does have a tag restriction and the machine is tagged with the same tag. | false | false |  |
| SecureIcaRequired | Changes whether the desktop rule requires the SecureICA protocol for desktop sessions launched using the entitlement.<br>A null value indicates that the equivalent setting from the rule's desktop group is used. | false | false |  |
| SessionReconnection | Defines reconnection (roaming) behavior for sessions launched using this rule. Possible values are:<br>Always, DisconnectedOnly, and SameEndpointOnly. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Entitlementpolicyrule
The desktop rule in the entitlement policy to be modified.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Entitlementpolicyrule
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.EntitlementPolicyRule object.
## Examples

### Example 1
```
C:\PS> Set-BrokerEntitlementPolicyRule 'Temp Workers' -AddIncludedUsers office\contractors
```
#### Description
Adds the user group OFFICE\\contractors to the Temp Workers desktop rule of the entitlement policy. This grants all members of that group an entitlement to a desktop session in the rule's associated desktop group. The session properties of the desktops obtained using the rule are determined by the rule's other properties.
### Example 2
```
C:\PS> Set-BrokerEntitlementPolicyRule 'Temp Workers' -Enabled $false
```
#### Description
Disables the Temp Workers desktop rule in the entitlement policy. This prevents further desktop sessions being launched using this rule until it is re-enabled. However, access to existing desktop sessions is not affected.
