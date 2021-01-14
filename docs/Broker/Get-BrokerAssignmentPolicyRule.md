
# Get-Brokerassignmentpolicyrule
Gets desktop rules from the site's assignment policy.
## Syntax
```
Get-BrokerAssignmentPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerAssignmentPolicyRule [[-Name] <String>] [-ColorDepth <ColorDepth>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IconUid <Int32>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-MaxDesktops <Int32>] [-Metadata <String>] [-PublishedName <String>] [-SecureIcaRequired <Boolean>] [-UUID <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns desktop rules matching the specified search criteria from the site's assignment policy. If no search criteria are specified, all desktop rules in the assignment policy are obtained.

A desktop rule in the assignment policy defines the users who are entitled to self-service persistent machine assignments from the rule's desktop group. A rule defines how many machines a user is allowed from the group for delivery of full desktop sessions.


### Brokerassignmentpolicyrule Object
The BrokerAssignmentPolicyRule object represents a single desktop rule within the site's assignment policy. It contains the following properties:


  * ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth?) The color depth of desktop sessions launched by the user from machines assigned to them by the rule. If null, the equivalent setting from the rule's desktop group is used.

  * Description (System.String) Optional description of the rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.

  * DesktopGroupUid (System.Int32) The unique ID of the desktop group to which the rule applies.

  * Enabled (System.Boolean) Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's assignment policy.

  * ExcludedUserFilterEnabled (System.Boolean) Indicates whether the excluded users filter is enabled. If the filter is disabled then any user entries in the filter are ignored when assignment policy rules are evaluated.

  * ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) The excluded users filter of the rule, that is, the users and groups who are explicitly denied entitlements to machine assignments from the rule's desktop group.

  * IconUid (System.Int32?) The unique ID of the icon used for the machine entitlement seen by the user or, after a machine is assigned by the rule, the icon for the desktop itself. If null, the equivalent setting from the rule's desktop group is used.

  * IncludedUserFilterEnabled (System.Boolean) Indicates whether the included users filter is enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly entitled to the machine assignments described by the rule.
    For rules that relate to RemotePC desktop groups however, if the included user filter is disabled, the rule is effectively disabled.

  * IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) The included users filter of the rule, that is, the users and groups who are entitled to machine assignments from the rule's desktop group.

  * MaxDesktops (System.Int32) The number of machines from the rule's desktop group to which a user is entitled. Where an entitlement is granted to a user group rather than an individual, the number of machines applies to each member of the user group independently.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) A collection of arbitrary key/value pairs that can be associated with the rule. The administrator can use these values for any purpose; they are not used by the site itself in any way.

  * Name (System.String) The administrative name of the rule. Each rule in the site's assignment policy must have a unique name (irrespective of whether they are desktop or application rules).

  * PublishedName (System.String) The published name of the desktop entitlement seen by the user or, after a machine is assigned by the rule, the published name of the desktop itself. If null, the equivalent setting from the rule's desktop group is used.

  * SecureIcaRequired (System.Boolean?) Indicates whether the rule requires the SecureICA protocol for desktop sessions launched using a machine assigned by the rule. If null, the equivalent setting from the rule's desktop group is used.

  * Uid (System.Int32) The unique ID of the rule itself.

  * UUID (System.Guid) UUID of the rule.


## Related Commands

* [New-BrokerAssignmentPolicyRule](./New-BrokerAssignmentPolicyRule/)
* [Set-BrokerAssignmentPolicyRule](./Set-BrokerAssignmentPolicyRule/)
* [Rename-BrokerAssignmentPolicyRule](./Rename-BrokerAssignmentPolicyRule/)
* [Remove-BrokerAssignmentPolicyRule](./Remove-BrokerAssignmentPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the desktop rule with the specified unique ID. | true | false |  |
| Name | Gets only desktop rules with the specified name. | false | false |  |
| ColorDepth | Gets only desktop rules with the specified color depth.<br>Valid values are \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | false |  |
| Description | Gets only desktop rules with the specified description. | false | false |  |
| DesktopGroupUid | Gets only desktop rules that apply to the desktop group with the specified unique ID. | false | false |  |
| Enabled | Gets only rules that are in the specified state, either enabled (\$true) or disabled (\$false). | false | false |  |
| ExcludedUser | Gets only desktop rules that have the specified user in their excluded users filter (whether the filter is enabled or not). | false | false |  |
| ExcludedUserFilterEnabled | Gets only desktop rules that have their excluded user filter enabled (\$true) or disabled (\$false). | false | false |  |
| IconUid | Gets only desktop rules using the icon with the specified unique ID. | false | false |  |
| IncludedUser | Gets only desktop rules that have the specified user in their included users filter (whether the filter is enabled or not). | false | false |  |
| IncludedUserFilterEnabled | Gets only desktop rules that have their included user filter enabled (\$true) or disabled (\$false). | false | false |  |
| MaxDesktops | Gets only desktop rules granting the specified number of machine assignment entitlements. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| PublishedName | Gets only desktop rules with the specified published name, that is, the desktop name that the end user sees. | false | false |  |
| SecureIcaRequired | Gets only desktop rules that require desktop sessions to machines assigned by the rule to use the SecureICA protocol (\$true) or not (\$false). | false | false |  |
| UUID | Gets rules with the specified value of UUID. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Assignmentpolicyrule
Get-BrokerAssignmentPolicyRule returns all assignment policy rules that match the specified selection criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerAssignmentPolicyRule
```
#### Description
Returns all desktop rules from the assignment policy. This offers a complete description of the current site's assignment policy with respect to machine assignment entitlements for delivery of desktop sessions from private desktop groups.
### Example 2
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Sales Support'

C:\PS> Get-BrokerAssignmentPolicyRule -DesktopGroupUid $dg.Uid
```
#### Description
Returns all rules in the assignment policy that give users entitlements to machine assignments in the Sales Support desktop group for delivery of full desktop sessions.
