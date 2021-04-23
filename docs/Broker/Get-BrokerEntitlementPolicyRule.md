
# Get-Brokerentitlementpolicyrule
Gets desktop rules from the site's entitlement policy.
## Syntax
```
Get-BrokerEntitlementPolicyRule [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerEntitlementPolicyRule [[-Name] <String>] [-BrowserName <String>] [-ColorDepth <ColorDepth>] [-Description <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-ExcludedUser <User>] [-ExcludedUserFilterEnabled <Boolean>] [-IconUid <Int32>] [-IncludedUser <User>] [-IncludedUserFilterEnabled <Boolean>] [-LeasingBehavior <LeasingBehavior>] [-MaxPerEntitlementInstances <Int32>] [-Metadata <String>] [-PublishedName <String>] [-RestrictToTag <String>] [-SecureIcaRequired <Boolean>] [-SessionReconnection <SessionReconnection>] [-UUID <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns desktop rules matching the specified search criteria from the site's entitlement policy. If no search criteria are specified, all desktop rules in the entitlement policy are obtained.

A desktop rule in the entitlement policy defines the users who are allowed per-session access to a machine from the rule's associated desktop group to run a full desktop session.


### Brokerentitlementpolicyrule Object
The BrokerEntitlementPolicyRule object represents a single desktop rule within the site's entitlement policy. It contains the following properties:


  * BrowserName (System.String) Site-wide unique name identifying this desktop entitlement to other components (for example StoreFront).

  * ColorDepth (Citrix.Broker.Admin.SDK.ColorDepth?) The color depth of any desktop session launched by the user from the entitlement. If null, the equivalent setting from the rule's desktop group is used.

  * Description (System.String) Optional description of the rule. The text may be visible to the end user, for example, as a tooltip associated with the desktop entitlement.

  * DesktopGroupUid (System.Int32) The unique ID of the desktop group to which the rule applies.

  * Enabled (System.Boolean) Indicates whether the rule is enabled. A disabled rule is ignored when evaluating the site's entitlement policy.

  * ExcludedUserFilterEnabled (System.Boolean) Indicates whether the excluded users filter is enabled. If the filter is disabled then any user entries in the filter are ignored when entitlement policy rules are evaluated.

  * ExcludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) The excluded users filter of the rule, that is, the users and groups who are explicitly denied an entitlement to a desktop session from this rule.

  * IconUid (System.Int32?) The unique ID of the icon used to display the desktop entitlement to the user. If null, the equivalent setting from the rule's desktop group is used.

  * IncludedUserFilterEnabled (System.Boolean) Indicates whether the included users filter is enabled. If the filter is disabled then any user who satisfies the requirements of the access policy is implicitly granted an entitlement to a desktop session by the rule.

  * IncludedUsers (Citrix.Broker.Admin.SDK.ChbUser\[\]) The included users filter of the rule, that is, the users and groups who are granted an entitlement to a desktop session by the rule.

  * LeasingBehavior (Citrix.Broker.Admin.SDK.LeasingBehavior) Defines the desired connection leasing behavior applied to sessions launched using this entitlement. Possible values are: Allowed and Disallowed.

  * MaxPerEntitlementInstances (System.Int32) Maximum allowed concurrently running instances of the desktop associated with this entitlement in the site . A value of zero allows unlimited usage.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) A collection of arbitrary key/value pairs that can be associated with the rule. The administrator can use these values for any purpose; they are not used by the site itself in any way.

  * Name (System.String) The administrative name of the rule. Each rule in the site's entitlement policy must have a unique name (irrespective of whether they are desktop or application rules).

  * PublishedName (System.String) The name of the desktop session entitlement as seen by the user. If null, the equivalent setting from the rule's desktop group is used.

  * RestrictToTag (System.String) Optional tag that may be used further to restrict which machines may be made accessible to a user by an entitlement policy rule. A machine may be made accessible by an entitlement policy rule only if either the rule has no tag restriction or the rule does have a tag restriction and the machine is tagged with the same tag.

  * SecureIcaRequired (System.Boolean?) Indicates whether the rule requires the SecureICA protocol for desktop sessions launched using the entitlement. If null, the equivalent setting from the rule's desktop group is used.

  * SessionReconnection (Citrix.Broker.Admin.SDK.SessionReconnection) Defines reconnection (roaming) behavior for sessions launched using this rule. Possible values are: Always, DisconnectedOnly, and SameEndpointOnly.

  * Uid (System.Int32) The unique ID of the rule itself.

  * UUID (System.Guid) UUID of the rule.


## Related Commands

* [New-BrokerEntitlementPolicyRule](./New-BrokerEntitlementPolicyRule/)
* [Set-BrokerEntitlementPolicyRule](./Set-BrokerEntitlementPolicyRule/)
* [Rename-BrokerEntitlementPolicyRule](./Rename-BrokerEntitlementPolicyRule/)
* [Remove-BrokerEntitlementPolicyRule](./Remove-BrokerEntitlementPolicyRule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the desktop rule with the specified unique ID. | true | false |  |
| Name | Gets only desktop rules with the specified name. | false | false |  |
| BrowserName | Gets only desktop rules with browser names matching the specified name. | false | false |  |
| ColorDepth | Gets only desktop rules with the specified color depth.<br>Valid values are \$null, FourBit, EightBit, SixteenBit, and TwentyFourBit. | false | false |  |
| Description | Gets only desktop rules with the specified description. | false | false |  |
| DesktopGroupUid | Gets only desktop rules that apply to the desktop group with the specified unique ID. | false | false |  |
| Enabled | Gets only desktop rules that are in the specified state, either enabled (\$true), or disabled (\$false). | false | false |  |
| ExcludedUser | Gets only desktop rules that have the specified user in their excluded users filter (whether the filter is enabled or not). | false | false |  |
| ExcludedUserFilterEnabled | Gets only desktop rules that have their excluded user filter enabled (\$true) or disabled (\$false). | false | false |  |
| IconUid | Gets only desktop rules using the icon with the specified unique ID. | false | false |  |
| IncludedUser | Gets only desktop rules that have the specified user in their included users filter (whether the filter is enabled or not). | false | false |  |
| IncludedUserFilterEnabled | Gets only desktop rules that have their included user filter enabled (\$true) or disabled (\$false). | false | false |  |
| LeasingBehavior | Gets only application rules with the specified connection leasing behavior. Possible values are:<br>Allowed and Disallowed. | false | false |  |
| MaxPerEntitlementInstances | Maximum allowed concurrently running instances of the desktop associated with this entitlement in the site . A value of zero allows unlimited usage. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| PublishedName | Gets only desktop rules with the specified published name, that is, the desktop session entitlement name that the end user sees. | false | false |  |
| RestrictToTag | Gets only desktop rules with the specified tag restriction. | false | false |  |
| SecureIcaRequired | Gets only desktop rules that require the desktop session to use the SecureICA protocol (\$true) or not (\$false). | false | false |  |
| SessionReconnection | Gets only desktop rules with the specified session reconnection behavior. Possible values are:<br>Always, DisconnectedOnly, and SameEndpointOnly. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Entitlementpolicyrule
Get-BrokerEntitlementPolicyRule returns all desktop entitlement policy rules that match the specified selection criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerEntitlementPolicyRule
```
#### Description
Returns all desktop rules from the entitlement policy. This offers a complete description of the current site's entitlement policy with respect to desktops published from shared desktop groups.
### Example 2
```
C:\PS> $dg = Get-BrokerDesktopGroup 'Customer Support'

C:\PS> Get-BrokerEntitlementPolicyRule -DesktopGroupUid $dg.Uid
```
#### Description
Returns all desktop rules in the entitlement policy that give users entitlements to desktop sessions in the Customer Support desktop group.
