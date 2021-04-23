
# New-Brokerappentitlementpolicyrule
Creates a new application rule in the site's entitlement policy.
## Syntax
```
New-BrokerAppEntitlementPolicyRule [-Name] <String> -DesktopGroupUid <Int32> [-Description <String>] [-Enabled <Boolean>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LeasingBehavior <LeasingBehavior>] [-SessionReconnection <SessionReconnection>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerAppEntitlementPolicyRule cmdlet adds a new application rule to the site's entitlement policy.

An application rule in the entitlement policy defines the users who are allowed per-session access to a machine to run one or more applications published from the rule's desktop group.

The following constraints apply when creating an application entitlement rule for a desktop group:


* The group's desktop kind must be Shared
* The group's delivery type must be AppsOnly or DesktopsAndApps
* Only a single application rule can apply to a given group

When a user selects an application published from a shared group, a machine is selected from the group on which to run the application. No permanent association exists between the user and the selected machine; once the session ends the association also ends.

Even though only a single application entitlement and therefore session can be defined for a group, the user can still run multiple applications from the group because the applications run within the same session.


## Related Commands

* [Get-BrokerAppEntitlementPolicyRule](./Get-BrokerAppEntitlementPolicyRule/)
* [Set-BrokerAppEntitlementPolicyRule](./Set-BrokerAppEntitlementPolicyRule/)
* [Rename-BrokerAppEntitlementPolicyRule](./Rename-BrokerAppEntitlementPolicyRule/)
* [Remove-BrokerAppEntitlementPolicyRule](./Remove-BrokerAppEntitlementPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the administrative name of the new application rule. Each rule in the site's entitlement policy must have a unique name (irrespective of whether they are desktop or application rules). | true | true (ByPropertyName) |  |
| DesktopGroupUid | Specifies the unique ID of the desktop group to which the new application rule applies. | true | true (ByPropertyName) |  |
| Description | Specifies an optional description of the new application rule. The text is purely informational for the administrator, it is never visible to the end user. | false | true (ByPropertyName) | null |
| Enabled | Specifies whether the new application rule is initially enabled. A disabled rule is ignored when evaluating the site's entitlement policy. | false | true (ByPropertyName) | true |
| ExcludedUserFilterEnabled | Specifies whether the excluded users filter is initially enabled. If the filter is disabled then any user entries in the filter are ignored when entitlement policy rules are evaluated. | false | true (ByPropertyName) | false |
| ExcludedUsers | Specifies the excluded users filter of the application rule, that is, the users and groups who are explicitly denied entitlements to published applications from the desktop group.<br>This can be used to exclude users or groups who would otherwise gain access by groups specified in the included users filter. | false | true (ByPropertyName) | (empty list) |
| IncludedUserFilterEnabled | Specifies whether the included users filter is initially enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to an application session by the new rule.<br>Users who would be implicitly granted access when the filter is disabled can still be explicitly denied access using the excluded users filter. | false | true (ByPropertyName) | true |
| IncludedUsers | Specifies the included users filter of the application rule, that is, the users and groups who are granted an entitlement to an application session by the new rule.<br>If a user appears explicitly in the excluded users filter of the rule or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter. | false | true (ByPropertyName) | (empty list) |
| LeasingBehavior | Defines the desired connection leasing behavior applied to sessions launched using this entitlement. Possible values are:<br>Allowed and Disallowed.<br>The Allowed value indicates that connection leasing should behave normally. The Disallowed value prevents users from launching or reconnecting to sessions using this entitlement while connection leasing is active (typically during a database outage). | false | true (ByPropertyName) | Allowed |
| SessionReconnection | Defines reconnection (roaming) behavior for sessions launched using this rule. Possible values are:<br>Always, DisconnectedOnly, and SameEndpointOnly. | false | true (ByPropertyName) | Always |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Appentitlementpolicyrule
New-BrokerAppEntitlementPolicyRule returns the newly created application rule in the entitlement policy.
## Examples

### Example 1
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'

C:\PS> New-BrokerAppEntitlementPolicyRule 'UK Office' -DesktopGroupUid $dg.Uid -IncludedUsers support\uk-staff
```
#### Description
Creates an application rule in the entitlement policy that entitles all members of the SUPPORT\\uk-staff group to a machine for running applications published from the Customer Support desktop group.
