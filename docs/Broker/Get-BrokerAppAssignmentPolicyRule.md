
# Get-Brokerappassignmentpolicyrule
Gets application rules from the site's assignment policy.
## Syntax
```
Get-BrokerAppAssignmentPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerAppAssignmentPolicyRule [[-Name] <String>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns application rules matching the specified search criteria from the site's assignment policy. If no search criteria are specified, all application rules in the assignment policy are obtained.

An application rule in the assignment policy defines the users who are entitled to a self-service persistent machine assignment from the rule's desktop group; once assigned the machine can run one or more applications published from the group.


### Brokerappassignmentpolicyrule Object
The BrokerAppAssignmentPolicyRule object represents a single application rule within the site's assignment policy. It contains the following properties:


  * Description (System.String) An optional description of the rule. The text is purely informational for the administrator, it is never visible to the end user.

  * DesktopGroupUid (System.Int32) The unique ID of the desktop group to which the rule applies.

  * Enabled (System.Boolean) Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's assignment policy.

  * ExcludedUserFilterEnabled (System.Boolean) Indicates whether the excluded users filter is enabled. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated.

  * ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) The excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a machine assignment from the rule's desktop group.

  * IncludedUserFilterEnabled (System.Boolean) Indicates whether the included users filter is enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly entitled to the machine assignment described by the rule.

  * IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) The included users filter of the rule, that is, the users and groups who are entitled to a machine assignment from the rule's desktop group.

  * Name (System.String) The administrative name of the rule. Each rule in the site's assignment policy must have a unique name (irrespective of whether they are desktop or application rules).

  * Uid (System.Int32) The unique ID of the rule itself.


## Related Commands

* [New-BrokerAppAssignmentPolicyRule](./New-BrokerAppAssignmentPolicyRule/)
* [Set-BrokerAppAssignmentPolicyRule](./Set-BrokerAppAssignmentPolicyRule/)
* [Rename-BrokerAppAssignmentPolicyRule](./Rename-BrokerAppAssignmentPolicyRule/)
* [Remove-BrokerAppAssignmentPolicyRule](./Remove-BrokerAppAssignmentPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the application rule with the specified unique ID. | true | false |  |
| Name | Gets only application rules with the specified name. | false | false |  |
| Description | Gets only application rules with the specified description. | false | false |  |
| DesktopGroupUid | Gets only application rules that apply to the desktop group with the specified unique ID. | false | false |  |
| Enabled | Gets only application rules that are in the specified state, either enabled (\$true) or disabled (\$false). | false | false |  |
| ExcludedUser | Gets only application rules that have the specified user in their excluded users filter (whether the filter is enabled or not) | false | false |  |
| ExcludedUserFilterEnabled | Gets only application rules that have their excluded user filter enabled (\$true) or disabled (\$false). | false | false |  |
| IncludedUser | Gets only application rules that have the specified user in their included users filter (whether the filter is enabled or not). | false | false |  |
| IncludedUserFilterEnabled | Gets only application rules that have their included user filter enabled (\$true) or disabled (\$false). | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Appassignmentpolicyrule
Get-BrokerAppAssignmentPolicyRule returns all application rules in the assignment policy that match the specified selection criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerAppAssignmentPolicyRule
```
#### Description
Returns all application rules from the assignment policy. This offers a complete description of the current site's assignment policy with respect to machine assignment entitlements for delivery of application sessions from private desktop groups.
### Example 2
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'

C:\PS> Get-BrokerAppAssignmentPolicyRule -DesktopGroupUid $dg.Uid
```
#### Description
Returns the rule in the assignment policy that gives users entitlements to machine assignments in the Sales Support desktop group for delivery of application sessions.
