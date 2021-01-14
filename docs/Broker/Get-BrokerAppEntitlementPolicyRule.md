
# Get-Brokerappentitlementpolicyrule
Gets application rules from the site's entitlement policy.
## Syntax
```
Get-BrokerAppEntitlementPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerAppEntitlementPolicyRule [[-Name] <String>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-LeasingBehavior <LeasingBehavior>] [-SessionReconnection <SessionReconnection>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns application rules matching the specified search criteria from the site's entitlement policy. If no search criteria are specified, all application rules in the entitlement policy are obtained.

An application rule in the entitlement policy defines the users who are allowed per-session access to a machine to run one or more applications published from the rule's desktop group.


### Brokerappentitlementpolicyrule Object
The BrokerAppEntitlementPolicyRule object represents a single application rule within the site's entitlement policy. It contains the following properties:


  * Description (System.String) Optional description of the rule. The text is purely informational for the administrator, it is never visible to the end user.

  * DesktopGroupUid (System.Int32) The unique ID of the desktop group to which the rule applies.

  * Enabled (System.Boolean) Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's entitlement policy.

  * ExcludedUserFilterEnabled (System.Boolean) Indicates whether the excluded users filter of the rule is enabled. If the filter is disabled then any user entries in the filter are ignored when entitlement policy rules are evaluated.

  * ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) The excluded users filter of the rule, that is, the users and groups who are explicitly denied entitlements to use published applications from the associated desktop group.

  * IncludedUserFilterEnabled (System.Boolean) Indicates whether the included users filter of the rule is enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to an application session by the rule.

  * IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) The included users filter of the rule, that is, the users and groups who are granted an entitlement to an application session by the rule.
    If a user appears explicitly in the excluded users filter of the rule or is a member of a group that appears in the excluded users filter, no entitlement is granted whether or not the user appears in the included users filter.

  * LeasingBehavior (Citrix.Broker.Admin.SDK.LeasingBehavior) Defines the desired connection leasing behavior applied to sessions launched using this entitlement. Possible values are: Allowed and Disallowed.

  * Name (System.String) The administrative name of the rule. Each rule in the site's entitlement policy must have a unique name (irrespective of whether they are desktop or application rules).

  * SessionReconnection (Citrix.Broker.Admin.SDK.SessionReconnection) Defines reconnection (roaming) behavior for sessions launched using this rule. Possible values are: Always, DisconnectedOnly, and SameEndpointOnly.

  * Uid (System.Int32) The unique ID of the rule itself.


## Related Commands

* [New-BrokerAppEntitlementPolicyRule](./New-BrokerAppEntitlementPolicyRule/)
* [Set-BrokerAppEntitlementPolicyRule](./Set-BrokerAppEntitlementPolicyRule/)
* [Rename-BrokerAppEntitlementPolicyRule](./Rename-BrokerAppEntitlementPolicyRule/)
* [Remove-BrokerAppEntitlementPolicyRule](./Remove-BrokerAppEntitlementPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the application rule with the specified unique ID. | true | false |  |
| Name | Gets only application rules with the specified name. | false | false |  |
| Description | Gets only application rules with the specified description. | false | false |  |
| DesktopGroupUid | Gets only the application rule that applies to the desktop group with the specified unique ID. | false | false |  |
| Enabled | Gets only application rules that are in the specified state, either enabled (\$true), or disabled (\$false). | false | false |  |
| ExcludedUser | Gets only application rules that have the specified user in their excluded users filter (whether the filter is enabled or not). | false | false |  |
| ExcludedUserFilterEnabled | Gets only application rules that have their excluded user filter enabled (\$true) or disabled (\$false). | false | false |  |
| IncludedUser | Gets only application rules that have the specified user in their included users filter (whether the filter is enabled or not). | false | false |  |
| IncludedUserFilterEnabled | Gets only application rules that have their included user filter enabled (\$true) or disabled (\$false). | false | false |  |
| LeasingBehavior | Gets only application rules with the specified connection leasing behavior. Possible values are:<br>Allowed and Disallowed. | false | false |  |
| SessionReconnection | Gets only application rules with the specified session reconnection behavior. Possible values are:<br>Always, DisconnectedOnly, and SameEndpointOnly. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Appentitlementpolicyrule
Get-BrokerAppEntitlementPolicyRule returns all application rules from the entitlement policy that match the specified selection criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerAppEntitlementPolicyRule
```
#### Description
Returns all application rules from the entitlement policy. This offers a complete description of the current site's entitlement policy with respect to application entitlements from shared desktop groups.
### Example 2
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'

C:\PS> Get-BrokerAppEntitlementPolicyRule -DesktopGroupUid $dg.Uid
```
#### Description
Returns the application rule in the entitlement policy that grants users an entitlement to application sessions in the Customer Support desktop group.
