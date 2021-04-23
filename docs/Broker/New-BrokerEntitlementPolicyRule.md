
# New-Brokerentitlementpolicyrule
Creates a new desktop rule in the site's entitlement policy.
## Syntax
```
New-BrokerEntitlementPolicyRule [-Name] <String> -DesktopGroupUid <Int32> [-ColorDepth <ColorDepth>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IconUid <Int32>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LeasingBehavior <LeasingBehavior>] [-MaxPerEntitlementInstances <Int32>] [-PublishedName <String>] [-RestrictToTag <String>] [-SecureIcaRequired <Boolean>] [-SessionReconnection <SessionReconnection>] [-UUID <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerEntitlementPolicyRule cmdlet adds a new desktop rule to the site's entitlement policy.

A desktop rule in the entitlement policy defines the users who are allowed per-session access to a machine from the rule's associated desktop group to run a full desktop session.

The following constraints apply when creating a desktop entitlement rule for a desktop group:


* The group's desktop kind must be Shared
* The group's delivery type must be DesktopsOnly or DesktopsAndApps

When a user selects a desktop entitlement published from a shared group, a machine is selected from the group on which to run the desktop session. No permanent association exists between the user and the selected machine; once the session ends the association also ends.

Multiple desktop rules in the entitlement policy can apply to the same desktop group. Where a user is granted an entitlement by more than one rule for the same group, they can use as many desktop sessions at the same time as they have entitlements.


## Related Commands

* [Get-BrokerEntitlementPolicyRule](./Get-BrokerEntitlementPolicyRule/)
* [Set-BrokerEntitlementPolicyRule](./Set-BrokerEntitlementPolicyRule/)
* [Rename-BrokerEntitlementPolicyRule](./Rename-BrokerEntitlementPolicyRule/)
* [Remove-BrokerEntitlementPolicyRule](./Remove-BrokerEntitlementPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the administrative name of the new desktop rule. Each rule in the site's entitlement policy must have a unique name (irrespective of whether they are desktop or application rules). | true | true (ByPropertyName) |  |
| DesktopGroupUid | Specifies the unique ID of the desktop group to which the new desktop rule applies. | true | true (ByPropertyName) |  |
| ColorDepth | Specifies the color depth of any desktop sessions launched by a user from this entitlement.<br>Valid values are \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| Description | Specifies an optional description of the new desktop rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| Enabled | Specifies whether the new desktop rule is initially enabled. A disabled rule is ignored when evaluating the site's entitlement policy. | false | true (ByPropertyName) | true |
| ExcludedUserFilterEnabled | Specifies whether the excluded users filter is initially enabled. If the filter is disabled then any user entries in the filter are ignored when entitlement policy rules are evaluated. | false | true (ByPropertyName) | false |
| ExcludedUsers | Specifies the excluded users filter of the desktop rule, that is, the users and groups who are explicitly denied an entitlement to a desktop session from the new rule.<br>This can be used to exclude users or groups who would otherwise gain access by groups specified in the included users filter. | false | true (ByPropertyName) | (empty list) |
| IconUid | Specifies the unique ID of the icon used to display the desktop session entitlement to the user.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| IncludedUserFilterEnabled | Specifies whether the included users filter is initially enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a desktop session by the new rule.<br>Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter. | false | true (ByPropertyName) | true |
| IncludedUsers | Specifies the included users filter of the rule, that is, the users and groups who are granted an entitlement to a desktop session by the new rule.<br>If a user appears explicitly in the excluded users filter of the rule or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter. | false | true (ByPropertyName) | (empty list) |
| LeasingBehavior | Defines the desired connection leasing behavior applied to sessions launched using this entitlement. Possible values are:<br>Allowed and Disallowed.<br>The Allowed value indicates that connection leasing should behave normally. The Disallowed value prevents users from launching or reconnecting to sessions using this entitlement while connection leasing is active (typically during a database outage). | false | true (ByPropertyName) | Allowed |
| MaxPerEntitlementInstances | Maximum allowed concurrently running instances of the desktop associated with this entitlement in the site . A value of zero allows unlimited usage. | false | true (ByPropertyName) | 0 |
| PublishedName | The name of the new desktop session entitlement as seen by the user.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| RestrictToTag | Optional tag that may be used further to restrict which machines may be made accessible to a user by an entitlement policy rule. A machine may be made accessible by an entitlement policy rule only if either the rule has no tag restriction or the rule does have a tag restriction and the machine is tagged with the same tag. | false | true (ByPropertyName) | null |
| SecureIcaRequired | Specifies whether the new desktop rule requires the SecureICA protocol for desktop sessions launched using the entitlement.<br>The default null value indicates that the equivalent setting from the rule's desktop group is used. | false | true (ByPropertyName) | null (dynamically inherited from the desktop group) |
| SessionReconnection | Defines reconnection (roaming) behavior for sessions launched using this rule. Possible values are:<br>Always, DisconnectedOnly, and SameEndpointOnly. | false | true (ByPropertyName) | Always |
| UUID | An optional GUID for this rule. | false | true (ByPropertyName) | A new GUID is generated if none is supplied. |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Entitlementpolicyrule
New-BrokerEntitlementPolicyRule returns the newly created desktop rule in the entitlement policy.
## Examples

### Example 1
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'

C:\PS> New-BrokerEntitlementPolicyRule 'UK Office' -DesktopGroupUid $dg.Uid -IncludedUsers support\uk-staff -PublishedName 'Support Desktop'
```
#### Description
Creates an desktop rule in the entitlement policy that entitles all members of the SUPPORT\\uk-staff group to a desktop session from the Customer Support desktop group. The desktop entitlement name seen by users is Support Desktop.
