
# New-Brokeraccesspolicyrule
Creates a new rule in the site's access policy.
## Syntax
```
New-BrokerAccessPolicyRule [-Name] <String> -DesktopGroupUid <Int32> [-AllowedConnections <AllowedConnection>] [-AllowedProtocols <String[]>] [-AllowedUsers <AllowedUser>] [-AllowRestart <Boolean>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedClientIPFilterEnabled <Boolean>] [-ExcludedClientIPs <IPAddressRange[]>] [-ExcludedClientNameFilterEnabled <Boolean>] [-ExcludedClientNames <String[]>] [-ExcludedSmartAccessFilterEnabled <Boolean>] [-ExcludedSmartAccessTags <String[]>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-HdxSslEnabled <Boolean>] [-IncludedClientIPFilterEnabled <Boolean>] [-IncludedClientIPs <IPAddressRange[]>] [-IncludedClientNameFilterEnabled <Boolean>] [-IncludedClientNames <String[]>] [-IncludedSmartAccessFilterEnabled <Boolean>] [-IncludedSmartAccessTags <String[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerAccessPolicyRule [-Name] <String> -IncludedDesktopGroups <DesktopGroup[]> [-IncludedDesktopGroupFilterEnabled <Boolean>] [-AllowedConnections <AllowedConnection>] [-AllowedProtocols <String[]>] [-AllowedUsers <AllowedUser>] [-AllowRestart <Boolean>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedClientIPFilterEnabled <Boolean>] [-ExcludedClientIPs <IPAddressRange[]>] [-ExcludedClientNameFilterEnabled <Boolean>] [-ExcludedClientNames <String[]>] [-ExcludedSmartAccessFilterEnabled <Boolean>] [-ExcludedSmartAccessTags <String[]>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-HdxSslEnabled <Boolean>] [-IncludedClientIPFilterEnabled <Boolean>] [-IncludedClientIPs <IPAddressRange[]>] [-IncludedClientNameFilterEnabled <Boolean>] [-IncludedClientNames <String[]>] [-IncludedSmartAccessFilterEnabled <Boolean>] [-IncludedSmartAccessTags <String[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerAccessPolicyRule cmdlet adds a new rule to the site's access policy.

An access policy rule defines a set of connection filters and access control rights relating to a desktop group. These allow fine-grained control of what access is granted to a desktop group based on details of, for example, a user's endpoint device, its address, and the user's identity.

Multiple rules in the access policy can apply to the same desktop group.

For a user to gain access to a desktop group via a rule their connection must match all its enabled include filters, and none of its enabled exclude filters. In addition, for a user to be able to launch a desktop or application resource session from the desktop group, they must have an entitlement to use the resource granted by the entitlement or assignment policies, or by direct machine assignment.


## Related Commands

* [Get-BrokerAccessPolicyRule](./Get-BrokerAccessPolicyRule/)
* [Set-BrokerAccessPolicyRule](./Set-BrokerAccessPolicyRule/)
* [Rename-BrokerAccessPolicyRule](./Rename-BrokerAccessPolicyRule/)
* [Remove-BrokerAccessPolicyRule](./Remove-BrokerAccessPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the administrative name of the new rule. Each rule within the site's access policy must have a unique name. | true | true (ByPropertyName) |  |
| DesktopGroupUid | Specifies the desktop group to which the new rule applies. | true | true (ByPropertyName) |  |
| IncludedDesktopGroups | This parameter is supported for backward compatibility only. If used only a single desktop group UID can be specified.<br>The IncludedDesktopGroups and IncludedDesktopGroupFilterEnabled parameters have been superseded by the DesktopGroupUid parameter. | true | true (ByPropertyName) | (empty list) |
| AllowedConnections | Specifies whether connections must be local or via Access Gateway, and if so whether specified SmartAccess tags must be provided by Access Gateway with the connection. This property forms part of the included SmartAccess tags filter.<br>Valid values are Filtered, NotViaAG, ViaAG and AnyViaAG.<br>For a detailed description of this property see "help about\_Broker\_AccessPolicy". | false | true (ByPropertyName) | Filtered |
| AllowedProtocols | Specifies the protocols (for example HDX, RDP) available to the user for sessions delivered from the new rule's desktop group. If the user gains access to a desktop group by multiple rules, the allowed protocol list is the combination of the protocol lists from all those rules.<br>If the protocol list is empty, access to the desktop group is implicitly denied. | false | true (ByPropertyName) | HDX |
| AllowedUsers | Specifies the behavior of the included users filter of the new rule. This can restrict access to a list of named users or groups, allow access to any authenticated user, any user (whether authenticated or not), or only non-authenticated users. For a detailed description of this property see "help about\_Broker\_AccessPolicy".<br>Valid values are Filtered, AnyAuthenticated, Any, AnonymousOnly and FilteredOrAnonymous. | false | true (ByPropertyName) | Filtered |
| AllowRestart | Specifies if the user can restart sessions delivered from the new rule's desktop group. Session restart is handled as follows: For sessions on single-session power-managed machines, the machine is powered off, and a new session launch request made; for sessions on multi-session machines, a logoff request is issued to the session, and a new session launch request made; otherwise the property is ignored. | false | true (ByPropertyName) | false |
| Description | Specifies an optional description of the new rule. The text is purely informational for the administrator, it is never visible to the end user. | false | true (ByPropertyName) |  |
| Enabled | Specifies whether the new rule is initially enabled. A disabled rule is ignored when evaluating the site's access policy. | false | true (ByPropertyName) | true |
| ExcludedClientIPFilterEnabled | Specifies whether the excluded client IP address filter is initially enabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | true (ByPropertyName) | false |
| ExcludedClientIPs | Specifies IP addresses of user devices explicitly denied access to the new rule's desktop group. Addresses can be specified as simple numeric addresses or as subnet masks (for example, 10.40.37.5 or 10.40.0.0/16). This property forms part of the excluded client IP address filter. | false | true (ByPropertyName) | (empty list) |
| ExcludedClientNameFilterEnabled | Specifies whether the excluded client names filter is initially enabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | true (ByPropertyName) | false |
| ExcludedClientNames | Specifies names of user devices explicitly denied access to the new rule's desktop group. This property forms part of the excluded client names filter. | false | true (ByPropertyName) | (empty list) |
| ExcludedSmartAccessFilterEnabled | Specifies whether the excluded SmartAccess tags filter is initially enabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | true (ByPropertyName) | false |
| ExcludedSmartAccessTags | Specifies SmartAccess tags which explicitly deny access to the new rule's desktop group if any occur in those provided by Access Gateway with the user's connection. This property forms part of the excluded SmartAccess tags filter. | false | true (ByPropertyName) | (empty list) |
| ExcludedUserFilterEnabled | Specifies whether the excluded users filter is initially enabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | true (ByPropertyName) | false |
| ExcludedUsers | Specifies any users and groups who are explicitly denied access to the new rule's desktop group. This property forms part of the excluded users filter. | false | true (ByPropertyName) | (empty list) |
| HdxSslEnabled | Indicates whether TLS encryption is enabled for sessions delivered from the rule's desktop group. | false | true (ByPropertyName) | \$false |
| IncludedClientIPFilterEnabled | Specifies whether the included client IP address filter is initially enabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | true (ByPropertyName) | false |
| IncludedClientIPs | Specifies IP addresses of user devices allowed access to the new rule's desktop group. Addresses can be specified as simple numeric addresses or as subnet masks (for example, 10.40.37.5 or 10.40.0.0/16). This property forms part of the included client IP address filter. | false | true (ByPropertyName) | (empty list) |
| IncludedClientNameFilterEnabled | Specifies whether the included client name filter is initially enabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | true (ByPropertyName) | false |
| IncludedClientNames | Specifies names of user devices allowed access to the new rule's desktop group. This property forms part of the included client names filter. | false | true (ByPropertyName) | (empty list) |
| IncludedSmartAccessFilterEnabled | Specifies whether the included SmartAccess tags filter is initially enabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | true (ByPropertyName) | false |
| IncludedSmartAccessTags | Specifies SmartAccess tags which grant access to the new rule's desktop group if any occur in those provided by Access Gateway with the user's connection. This property forms part of the excluded SmartAccess tags filter. | false | true (ByPropertyName) | (empty list) |
| IncludedUserFilterEnabled | Specifies whether the included users filter is initially enabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | true (ByPropertyName) | false |
| IncludedUsers | Specifies users and groups who are granted access to the new rule's desktop group. This property forms part of the included users filter. | false | true (ByPropertyName) | (empty list) |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| IncludedDesktopGroupFilterEnabled | This parameter is supported for backward compatibility only. If used the supplied value must be \$true.<br>The IncludedDesktopGroups and IncludedDesktopGroupFilterEnabled parameters have been superseded by the DesktopGroupUid parameter. | false | true (ByPropertyName) | true |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Accesspolicyrule
New-BrokerAccessPolicyRule returns the newly created access policy rule.
## Examples

### Example 1
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Tech Support'

C:\PS> New-BrokerAccessPolicyRule 'UK Tech Support' -IncludedUserFilterEnabled $true -IncludedUsers support\uk-staff -DesktopGroupUid $dg.Uid -AllowedProtocols 'HDX'
```
#### Description
Creates an access policy rule allowing access to the Tech Support desktop group for all users of the SUPPORT\\uk-staff group. Connections to desktop or application resources in the group can only be made using the HDX protocol.&lt;br&gt;For users to gain access to resources in the group also requires that, depending on the desktop kind of the group, appropriate assignment or entitlement policy rules, or explicit machine assignments exist.
