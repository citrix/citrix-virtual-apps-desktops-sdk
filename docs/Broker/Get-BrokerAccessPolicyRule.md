
# Get-Brokeraccesspolicyrule
Gets rules from the site's access policy.
## Syntax
```
Get-BrokerAccessPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerAccessPolicyRule [[-Name] <String>] [-AllowedConnections <AllowedConnection>] [-AllowedUsers <AllowedUser>] [-Description <String>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedClientIPFilterEnabled <Boolean>] [-ExcludedClientName <String>] [-ExcludedClientNameFilterEnabled <Boolean>] [-ExcludedSmartAccessFilterEnabled <Boolean>] [-ExcludedSmartAccessTag <String>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IncludedClientIPFilterEnabled <Boolean>] [-IncludedClientName <String>] [-IncludedClientNameFilterEnabled <Boolean>] [-IncludedSmartAccessFilterEnabled <Boolean>] [-IncludedSmartAccessTag <String>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-Metadata <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns rules matching the specified search criteria from the site's access policy. If no search criteria are specified, all rules in the access policy are obtained.

An access policy rule defines a set of connection filters and access control rights relating to a desktop group. These allow fine-grained control of what access is granted to a desktop group based on details of, for example, a user's endpoint device, its address, and the user's identity.


### Brokeraccesspolicyrule Object
A BrokerAccessPolicyRule object represents a single rule within the site's access policy. For a user to gain access to a desktop group via the rule their connection must match all its enabled include filters, and none of its enabled exclude filters. The object contains the following properties:


  * AllowedConnections (Citrix.Broker.Admin.SDK.AllowedConnection) Controls whether connections must be local or via Access Gateway, and if so whether specified SmartAccess tags must be provided by Access Gateway with the connection. This property forms part of the included SmartAccess tags filter.
    For a detailed description of this property see "help about\_Broker\_AccessPolicy".

  * AllowedProtocols (System.String\[\]) Protocols (for example HDX, RDP) available to the user for sessions delivered from the rule's desktop group. If the user gains access to a desktop group by multiple rules, the allowed protocol list is the combination of the protocol lists from all those rules.
    If the protocol list is empty, access to the desktop group is implicitly denied.

  * AllowedUsers (Citrix.Broker.Admin.SDK.AllowedUser) Controls the behavior of the included users filter. This can restrict access to a list of named users or groups, or allow access to any authenticated user. For a detailed description of this property see "help about\_Broker\_AccessPolicy".

  * AllowRestart (System.Boolean) Indicates if the user can restart sessions delivered from the rule's desktop group. Session restart is handled as follows: For sessions on single-session power-managed machines, the machine is powered off, and a new session launch request made; for sessions on multi-session machines, a logoff request is issued to the session, and a new session launch request made; otherwise the property is ignored.

  * Description (System.String) An optional description of the rule. The text is purely informational for the administrator, it is never visible to the end user.

  * DesktopGroupName (System.String) The name of the desktop group to which the rule applies.

  * DesktopGroupUid (System.Int32) The unique ID of the desktop group to which the rule applies.

  * Enabled (System.Boolean) Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's access policy.

  * ExcludedClientIPFilterEnabled (System.Boolean) Indicates whether the excluded client IP filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.

  * ExcludedClientIPs (Citrix.Broker.Admin.SDK.ChbIPAddressRange\[\]) IP addresses of user devices explicitly denied access to the rule's desktop group. Addresses can be specified as simple numeric addresses or as subnet masks (for example, 10.40.37.5 or 10.40.0.0/16). This property forms part of the excluded client IP address filter.

  * ExcludedClientNameFilterEnabled (System.Boolean) Indicates whether the excluded client name filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.

  * ExcludedClientNames (System.String\[\]) Names of user devices explicitly denied access to the rule's desktop group. This property forms part of the excluded client names filter.

  * ExcludedSmartAccessFilterEnabled (System.Boolean) Indicates whether the excluded SmartAccess tags filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.

  * ExcludedSmartAccessTags (System.String\[\]) SmartAccess tags which explicitly deny access to the rule's desktop group if any occur in those provided by Access Gateway with the user's connection. This property forms part of the excluded SmartAccess tags filter.

  * ExcludedUserFilterEnabled (System.Boolean) Indicates whether the excluded users filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.

  * ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) Users and groups who are explicitly denied access to the rule's desktop group. This property forms part of the excluded users filter.

  * HdxSslEnabled (System.Boolean) Indicates whether TLS encryption is enabled for sessions delivered from the rule's desktop group.

  * IncludedClientIPFilterEnabled (System.Boolean) Indicates whether the included client IP filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.

  * IncludedClientIPs (Citrix.Broker.Admin.SDK.ChbIPAddressRange\[\]) IP addresses of user devices allowed access to the rule's desktop group. Addresses can be specified as simple numeric addresses or as subnet masks (for example, 10.40.37.5 or 10.40.0.0/16). This property forms part of the included client IP address filter.

  * IncludedClientNameFilterEnabled (System.Boolean) Indicates whether the included client names filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.

  * IncludedClientNames (System.String\[\]) Names of user devices allowed access to the rule's desktop group. This property forms part of the included client names filter.

  * IncludedSmartAccessFilterEnabled (System.Boolean) Indicates whether the included SmartAccess tags filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.

  * IncludedSmartAccessTags (System.String\[\]) The SmartAccess tags which grant access to the rule's desktop group if any occur in those provided by Access Gateway with the user's connection. This property forms part of the excluded SmartAccess tags filter.

  * IncludedUserFilterEnabled (System.Boolean) Indicates whether the included users filter is enabled. If the filter is disabled it is ignored when the rule is evaluated.

  * IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) Users and groups who are granted access to the rule's desktop group. This property forms part of the included users filter.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) A collection of arbitrary key/value pairs that can be associated with the rule. The administrator can use these values for any purpose; they are not used by the site itself in any way.

  * Name (System.String) Administrative name of the rule. Each rule in the site's access policy must have a unique name.

  * Uid (System.Int32) Unique ID of the rule itself.


## Related Commands

* [New-BrokerAccessPolicyRule](./New-BrokerAccessPolicyRule/)
* [Set-BrokerAccessPolicyRule](./Set-BrokerAccessPolicyRule/)
* [Rename-BrokerAccessPolicyRule](./Rename-BrokerAccessPolicyRule/)
* [Remove-BrokerAccessPolicyRule](./Remove-BrokerAccessPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the rule with the specified unique ID. | true | false |  |
| Name | Gets only rules with the specified name. | false | false |  |
| AllowedConnections | Gets only rules that have the specified value in the AllowedConnections property of their included SmartAccess tags filter.<br>Valid values are Filtered, NotViaAG, ViaAG and AnyViaAG. | false | false |  |
| AllowedUsers | Gets only rules that have the specified value in the AllowedUsers property of their included users filter.<br>Valid values are Filtered, AnyAuthenticated, Any, AnonymousOnly and FilteredOrAnonymous. | false | false |  |
| Description | Gets only rules with the specified description. | false | false |  |
| DesktopGroupName | Gets only rules applying to desktop groups with names matching the specified name. | false | false |  |
| DesktopGroupUid | Gets only rules that apply to the desktop group with the specified unique ID. | false | false |  |
| Enabled | Gets only rules that are in the specified state, either enabled (\$true) or disabled (\$false). | false | false |  |
| ExcludedClientIPFilterEnabled | Gets only rules that have their excluded client IP address filter enabled (\$true) or disabled (\$false). | false | false |  |
| ExcludedClientName | Gets only rules that have the specified client name in their excluded client names filter (whether the filter is enabled or not). | false | false |  |
| ExcludedClientNameFilterEnabled | Gets only rules that have their excluded client name filter enabled (\$true) or disabled (\$false). | false | false |  |
| ExcludedSmartAccessFilterEnabled | Gets only rules that have their excluded SmartAccess tags filter enabled (\$true) or disabled (\$false). | false | false |  |
| ExcludedSmartAccessTag | Gets only rules that have the specified SmartAccess tag in their excluded SmartAccess tags filter (whether the filter is enabled or not). | false | false |  |
| ExcludedUser | Gets only rules that have the specified user in their excluded users filter (whether the filter is enabled or not). | false | false |  |
| ExcludedUserFilterEnabled | Gets only rules that have their excluded user filter enabled (\$true) or disabled (\$false). | false | false |  |
| IncludedClientIPFilterEnabled | Gets only rules that have their included client IP address filter enabled (\$true) or disabled (\$false). | false | false |  |
| IncludedClientName | Gets only rules that have the specified user device name in their included client names filter (whether the filter is enabled or not). | false | false |  |
| IncludedClientNameFilterEnabled | Gets only rules that have their included client name filter enabled (\$true) or disabled (\$false). | false | false |  |
| IncludedSmartAccessFilterEnabled | Gets only rules that have their included SmartAccess tags filter enabled (\$true) or disabled (\$false). | false | false |  |
| IncludedSmartAccessTag | Gets only rules that have the specified SmartAccess tag in their included SmartAccess tags filter (whether the filter is enabled or not). | false | false |  |
| IncludedUser | Gets only rules that have the specified user in their included users filter (whether the filter is enabled or not). | false | false |  |
| IncludedUserFilterEnabled | Gets only rules that have their included user filter enabled (\$true) or disabled (\$false). | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Accesspolicyrule
Get-BrokerAccessPolicyRule returns all access policy rules that match the specified selection criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerAccessPolicyRule
```
#### Description
Returns all access policy rules. This offers a complete description of the current site's access policy.
### Example 2
```
C:\PS> Get-BrokerAccessPolicyRule -Enabled $true -IncludedUser sales\tech-support
```
#### Description
Returns all rules that are both enabled and explicitly include the SALES\\tech-support group in their included users filter.
