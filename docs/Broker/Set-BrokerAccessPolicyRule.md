
# Set-Brokeraccesspolicyrule
Modifies an existing rule in the site's access policy.
## Syntax
```
Set-BrokerAccessPolicyRule [-InputObject] <AccessPolicyRule[]> [-PassThru] [-AddExcludedClientIPs <IPAddressRange[]>] [-AddExcludedClientNames <String[]>] [-AddExcludedSmartAccessTags <String[]>] [-AddExcludedUsers <User[]>] [-AddIncludedClientIPs <IPAddressRange[]>] [-AddIncludedClientNames <String[]>] [-AddIncludedSmartAccessTags <String[]>] [-AddIncludedUsers <User[]>] [-AllowedConnections <AllowedConnection>] [-AllowedProtocols <String[]>] [-AllowedUsers <AllowedUser>] [-AllowRestart <Boolean>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedClientIPFilterEnabled <Boolean>] [-ExcludedClientIPs <IPAddressRange[]>] [-ExcludedClientNameFilterEnabled <Boolean>] [-ExcludedClientNames <String[]>] [-ExcludedSmartAccessFilterEnabled <Boolean>] [-ExcludedSmartAccessTags <String[]>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-HdxSslEnabled <Boolean>] [-IncludedClientIPFilterEnabled <Boolean>] [-IncludedClientIPs <IPAddressRange[]>] [-IncludedClientNameFilterEnabled <Boolean>] [-IncludedClientNames <String[]>] [-IncludedSmartAccessFilterEnabled <Boolean>] [-IncludedSmartAccessTags <String[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-RemoveExcludedClientIPs <IPAddressRange[]>] [-RemoveExcludedClientNames <String[]>] [-RemoveExcludedSmartAccessTags <String[]>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedClientIPs <IPAddressRange[]>] [-RemoveIncludedClientNames <String[]>] [-RemoveIncludedSmartAccessTags <String[]>] [-RemoveIncludedUsers <User[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerAccessPolicyRule [-Name] <String> [-PassThru] [-AddExcludedClientIPs <IPAddressRange[]>] [-AddExcludedClientNames <String[]>] [-AddExcludedSmartAccessTags <String[]>] [-AddExcludedUsers <User[]>] [-AddIncludedClientIPs <IPAddressRange[]>] [-AddIncludedClientNames <String[]>] [-AddIncludedSmartAccessTags <String[]>] [-AddIncludedUsers <User[]>] [-AllowedConnections <AllowedConnection>] [-AllowedProtocols <String[]>] [-AllowedUsers <AllowedUser>] [-AllowRestart <Boolean>] [-Description <String>] [-Enabled <Boolean>] [-ExcludedClientIPFilterEnabled <Boolean>] [-ExcludedClientIPs <IPAddressRange[]>] [-ExcludedClientNameFilterEnabled <Boolean>] [-ExcludedClientNames <String[]>] [-ExcludedSmartAccessFilterEnabled <Boolean>] [-ExcludedSmartAccessTags <String[]>] [-ExcludedUserFilterEnabled <Boolean>] [-ExcludedUsers <User[]>] [-HdxSslEnabled <Boolean>] [-IncludedClientIPFilterEnabled <Boolean>] [-IncludedClientIPs <IPAddressRange[]>] [-IncludedClientNameFilterEnabled <Boolean>] [-IncludedClientNames <String[]>] [-IncludedSmartAccessFilterEnabled <Boolean>] [-IncludedSmartAccessTags <String[]>] [-IncludedUserFilterEnabled <Boolean>] [-IncludedUsers <User[]>] [-RemoveExcludedClientIPs <IPAddressRange[]>] [-RemoveExcludedClientNames <String[]>] [-RemoveExcludedSmartAccessTags <String[]>] [-RemoveExcludedUsers <User[]>] [-RemoveIncludedClientIPs <IPAddressRange[]>] [-RemoveIncludedClientNames <String[]>] [-RemoveIncludedSmartAccessTags <String[]>] [-RemoveIncludedUsers <User[]>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerAccessPolicyRule cmdlet modifies an existing rule in the site's access policy.

An access policy rule defines a set of connection filters and access control rights relating to a desktop group. These allow fine-grained control of what access is granted to a desktop group based on details of, for example, a user's endpoint device, its address, and the user's identity.

Changing a rule does not affect existing user sessions, but it may result in users being unable to launch new sessions, or reconnect to disconnected sessions if the change removes access to the desktop group delivering those sessions.


## Related Commands

* [New-BrokerAccessPolicyRule](./New-BrokerAccessPolicyRule/)
* [Get-BrokerAccessPolicyRule](./Get-BrokerAccessPolicyRule/)
* [Rename-BrokerAccessPolicyRule](./Rename-BrokerAccessPolicyRule/)
* [Remove-BrokerAccessPolicyRule](./Remove-BrokerAccessPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The access policy rule to be modified. | true | true (ByValue) |  |
| Name | The name of the access policy rule to be modified. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| AddExcludedClientIPs | Adds the specified user device IP addresses to the excluded client IP address filter of the rule.<br>See the ExcludedClientIPs parameter for more information. | false | false |  |
| AddExcludedClientNames | Adds the specified user device names to the excluded client names filter of the rule.<br>See the ExcludedClientNames parameter for more information. | false | false |  |
| AddExcludedSmartAccessTags | Adds the specified SmartAccess tags to the excluded SmartAccess tags filter of the rule.<br>See the ExcludedSmartAccessTags parameter for more information. | false | false |  |
| AddExcludedUsers | Adds the specified users and groups to the excluded users filter of the rule.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| AddIncludedClientIPs | Adds the specified user device IP addresses to the included client IP address filter of the rule.<br>See the IncludedClientIPs parameter for more information. | false | false |  |
| AddIncludedClientNames | Adds the specified user device names to the included client names filter of the rule.<br>See the IncludedClientNames parameter for more information. | false | false |  |
| AddIncludedSmartAccessTags | Adds the specified SmartAccess tags to the included SmartAccess tags filter of the rule.<br>See the IncludedSmartAccessTags parameter for more information. | false | false |  |
| AddIncludedUsers | Adds the specified users and groups to the included users filter of the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| AllowedConnections | Changes whether connections must be local or via Access Gateway, and if so whether specified SmartAccess tags must be provided by Access Gateway with the connection. This property forms part of the included SmartAccess tags filter.<br>Valid values are Filtered, NotViaAG, ViaAG and AnyViaAG.<br>For a detailed description of this property see "help about\_Broker\_AccessPolicy". | false | false |  |
| AllowedProtocols | Changes the protocols (for example HDX, RDP) available to the user for sessions delivered from the rule's desktop group. If the user gains access to a desktop group by multiple rules, the allowed protocol list is the combination of the protocol lists from all those rules.<br>If the protocol list is empty, access to the desktop group is implicitly denied. | false | false |  |
| AllowedUsers | Changes the behavior of the included users filter of the rule. This can restrict access to a list of named users or groups, allow access to any authenticated user, any user (whether authenticated or not), or only non-authenticated users. For a detailed description of this property see "help about\_Broker\_AccessPolicy".<br>Valid values are Filtered, AnyAuthenticated, Any, AnonymousOnly and FilteredOrAnonymous. | false | false |  |
| AllowRestart | Changes whether the user can restart sessions delivered from the rule's desktop group. Session restart is handled as follows: For sessions on single-session power-managed machines, the machine is powered off, and a new session launch request made; for sessions on multi-session machines, a logoff request is issued to the session, and a new session launch request made; otherwise the property is ignored. | false | false |  |
| Description | Changes the description of the rule. The text is purely informational for the administrator, it is never visible to the end user. | false | false |  |
| Enabled | Changes whether the rule is enabled or disabled. A disabled rule is ignored when evaluating the site's access policy. | false | false |  |
| ExcludedClientIPFilterEnabled | Changes whether the excluded client IP address filter is enabled or disabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | false |  |
| ExcludedClientIPs | Changes the IP addresses of user devices explicitly denied access to the rule's desktop group. Addresses can be specified as simple numeric addresses or as subnet masks (for example, 10.40.37.5 or 10.40.0.0/16). This property forms part of the excluded client IP address filter. | false | false |  |
| ExcludedClientNameFilterEnabled | Changes whether the excluded client names filter is enabled or disabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | false |  |
| ExcludedClientNames | Changes which names of user devices are explicitly denied access to the rule's desktop group. This property forms part of the excluded client names filter. | false | false |  |
| ExcludedSmartAccessFilterEnabled | Changes whether the excluded SmartAccess tags filter is enabled or disabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | false |  |
| ExcludedSmartAccessTags | Changes which SmartAccess tags explicitly deny access to the rule's desktop group if any occur in those provided by Access Gateway with the user's connection. This property forms part of the excluded SmartAccess tags filter. | false | false |  |
| ExcludedUserFilterEnabled | Changes whether the excluded users filter is enabled or disabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | false |  |
| ExcludedUsers | Changes which users and groups are explicitly denied access to the rule's desktop group. This property forms part of the excluded users filter. | false | false |  |
| HdxSslEnabled | Indicates whether TLS encryption is enabled for sessions delivered from the rule's desktop group. | false | false |  |
| IncludedClientIPFilterEnabled | Changes whether the included client IP address filter is enabled or disabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | false |  |
| IncludedClientIPs | Changes which IP addresses of user devices allowed access to the rule's desktop group. Addresses can be specified as simple numeric addresses or as subnet masks (for example, 10.40.37.5 or 10.40.0.0/16). This property forms part of the included client IP address filter. | false | false |  |
| IncludedClientNameFilterEnabled | Changes whether the included client name filter is enabled or disabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | false |  |
| IncludedClientNames | Changes which names of user devices are allowed access to the rule's desktop group. This property forms part of the included client names filter. | false | false |  |
| IncludedSmartAccessFilterEnabled | Changes whether the included SmartAccess tags filter is enabled or disabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | false |  |
| IncludedSmartAccessTags | Changes which SmartAccess tags grant access to the rule's desktop group if any occur in those provided by Access Gateway with the user's connection. This property forms part of the excluded SmartAccess tags filter. | false | false |  |
| IncludedUserFilterEnabled | Changes whether the included users filter is enabled or disabled. If the filter is disabled, it is ignored when the access policy rule is evaluated. | false | false |  |
| IncludedUsers | Changes which users and groups are granted access to the rule's desktop group. This property forms part of the included users filter. | false | false |  |
| RemoveExcludedClientIPs | Removes the specified user device IP addresses from the excluded client IP address filter of the rule.<br>See the ExcludedClientIPs parameter for more information. | false | false |  |
| RemoveExcludedClientNames | Removes the specified user device names from the excluded client names filter of the rule.<br>See the ExcludedClientNames parameter for more information. | false | false |  |
| RemoveExcludedSmartAccessTags | Removes the specified SmartAccess tags from the excluded SmartAccess tags filter of the rule.<br>See the ExcludedSmartAccessTags parameter for more information. | false | false |  |
| RemoveExcludedUsers | Removes the specified users and groups from the excluded users filter of the rule.<br>See the ExcludedUsers parameter for more information. | false | false |  |
| RemoveIncludedClientIPs | Removes the specified user device IP addresses from the included client IP address filter of the rule.<br>See the IncludedClientIPs parameter for more information. | false | false |  |
| RemoveIncludedClientNames | Removes the specified client names from the included client names filter of the rule.<br>See the IncludedClientNames parameter for more information. | false | false |  |
| RemoveIncludedSmartAccessTags | Removes the specified SmartAccess tags from the included SmartAccess tags filter of the rule.<br>See the IncludedSmartAccessTags parameter for more information. | false | false |  |
| RemoveIncludedUsers | Removes the specified users and groups from the included users filter of the rule.<br>See the IncludedUsers parameter for more information. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Accesspolicyrule
The access policy rule to be modified.
## Return Values

### None, Or Citrix.Broker.Admin.Sdk.Accesspolicyrule
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AccessPolicyRule object.
## Examples

### Example 1
```
C:\PS> Set-BrokerAccessPolicyRule 'Temp Staff' -AddIncludedUsers office\contractors
```
#### Description
Adds user group OFFICE\\contractors to the Temp Staff access policy rule. The resources that the group can access are dependent on the existing properties of the rule in addition to the site's assignment and entitlement policies.
### Example 2
```
C:\PS> Set-BrokerAccessPolicyRule 'Temp Staff' -ExcludedClientIPFilterEnabled $true -AddExcludedClientIPs '10.15.0.0/16' -AllowedConnections ViaAG
```
#### Description
Modifies the Temp Staff access policy rule to remove access to any user device with an IP address matching 10.15.0.0/16, and requires that all connections by the rule must come through Access Gateway (assuming that the included SmartAccess tags filter is enabled).
