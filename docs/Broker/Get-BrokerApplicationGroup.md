
# Get-Brokerapplicationgroup
Gets details of configured application groups.
## Syntax
```
Get-BrokerApplicationGroup [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerApplicationGroup [[-Name] <String>] [-AssociatedDesktopGroupPriority <Int32>] [-AssociatedDesktopGroupUid <Int32>] [-AssociatedDesktopGroupUUID <Guid>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserSID <String>] [-AssociatedUserUPN <String>] [-Description <String>] [-Enabled <Boolean>] [-Metadata <String>] [-RestrictToTag <String>] [-ScopeId <Guid>] [-ScopeName <String>] [-SessionSharingEnabled <Boolean>] [-SingleAppPerSession <Boolean>] [-Tag <String>] [-TenantId <Guid>] [-TotalApplications <Int32>] [-TotalMachines <Int32>] [-TotalMachinesWithTagRestriction <Int32>] [-UserFilterEnabled <Boolean>] [-UUID <Guid>] [-ApplicationUid <Int32>] [-DesktopGroupUid <Int32>] [-TagUid <Int32>] [-UserSID <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerApplicationGroup cmdlet returns application groups that have been configured as part of the site.

With no parameters, Get-BrokerApplicationGroup returns all the application groups that have been configured. You also can use the parameters of Get-BrokerApplicationGroup to filter the results to just application groups you're interested in. You can also identify application groups by their UIDs or their Names.

See about\_Broker\_Applications for more information.


### Brokerapplicationgroup Object
A BrokerApplicationGroup object represents a single application group that has been configured as part of the site. It has the following properties:


  * AssociatedDesktopGroupPriorities (System.Int32\[\]) List of associated desktop group priorities. This list is presented in the same order as AssociatedDesktopGroupUids and AssociatedDesktopGroupUUIDs.
    When launching an application an available machine from one of the associated desktop groups is selected. Desktop groups are searched for available machines in order of their priority.

  * AssociatedDesktopGroupUids (System.Int32\[\]) List of associated desktop group uids. Associated desktop groups is the list of desktop groups on which the application group is published. The list is sorted by priority, with the highest priority desktop group first.

  * AssociatedDesktopGroupUUIDs (System.Guid\[\]) List of associated desktop group UUIDs. Associated desktop groups is the list of desktop groups on which the application group is published. The list is sorted by priority, with the highest priority desktop group first.

  * AssociatedUserFullNames (System.String\[\]) List of associated users (full names). Associated users is the list of users who are given access using the application group/user mapping filter.

  * AssociatedUserNames (System.String\[\]) List of associated users (SAM names). Associated users is the list of users who are given access using the application group/user mapping filter.

  * AssociatedUserSIDs (System.String\[\]) List of associated users (SIDs). Associated users is the list of users who are given access using the application group/user mapping filter.

  * AssociatedUserUPNs (System.String\[\]) List of associated users (user principle names). Associated users is the list of users who are given access using the application group/user mapping filter.

  * Description (System.String) Optional application group description. This description is visible in Citrix Studio and can be used for any purpose. As with other facets of application groups, the description is not visible to end users.

  * Enabled (System.Boolean) Specifies whether or not the applications in this application group can be launched.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this application group.

  * Name (System.String) Name of this application group. The name is visible in Citrix Studio and uniquely identifies the application group. As with other facets of application groups, the name is not visible to end users.

  * RestrictToTag (System.String) Optional tag that may be used further to restrict which machines may be used for launching the application group's applications. A machine may be used by an application group if either the application group has no tag restriction or the application group does have a tag restriction and the machine is tagged with the same tag.

  * Scopes (Citrix.Fma.Sdk.DelegatedAdminInterfaces.ScopeReference\[\]) The list of the delegated admin scopes to which the application group belongs.

  * SessionSharingEnabled (System.Boolean) Whether applications in this application group can share sessions with applications in other application groups (or with applications that are not a member of an application group).
    Applications in the same application group can always share sessions with each other, unless session sharing has been disabled by other means.

  * SingleAppPerSession (System.Boolean) Indicates whether each application launched from this application group uses a new session or can share an existing one.

  * Tags (System.String\[\]) Tags associated with the application group.

  * TenantId (System.Guid?) Identity of tenant associated with application group. Not applicable (always blank) in non-multitenant sites.

  * TotalApplications (System.Int32) Number of applications in the application group.

  * TotalMachines (System.Int32) Total number of machines across all desktop groups on which the application group is published.

  * TotalMachinesWithTagRestriction (System.Int32) Total number of machines across all desktop groups on which the application group is published, and which are tagged with the tag given by the RestrictToTag property.
    The value of this property is always equal to or less than the value of the TotalMachines property. If RestrictToTag is \$null, then the properties' values are equal.

  * Uid (System.Int32) Uid of the application group.

  * UserFilterEnabled (System.Boolean) Whether the application group's user filter is enabled.

  * UUID (System.Guid) UUID of the application group.


## Related Commands

* [Add-BrokerApplicationGroup](./Add-BrokerApplicationGroup/)
* [New-BrokerApplicationGroup](./New-BrokerApplicationGroup/)
* [Remove-BrokerApplicationGroup](./Remove-BrokerApplicationGroup/)
* [Rename-BrokerApplicationGroup](./Rename-BrokerApplicationGroup/)
* [Set-BrokerApplicationGroup](./Set-BrokerApplicationGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the application group with the given Uid. | true | false |  |
| Name | Gets application groups whose name matches the supplied pattern. | false | false |  |
| AssociatedDesktopGroupPriority | Gets application groups with which a desktop group has been associated with the specified priority. | false | false |  |
| AssociatedDesktopGroupUid | Gets application groups which have been associated with the specified desktop group. The desktop group is identified by its Uid. | false | false |  |
| AssociatedDesktopGroupUUID | Gets application groups which have been associated with the specified desktop group. The desktop group is identified by its UUID. | false | false |  |
| AssociatedUserFullName | Gets application groups with an associated user identified by their user name (usually 'first-name last-name').<br>If the 'UserFilterEnabled' property is true then access to applications in the application group is restricted to those users only. Otherwise, access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserName | Gets application groups with an associated user identified by their user name (in the form 'domain\\user').<br>If the 'UserFilterEnabled' property is true then access to applications in the application group is restricted to those users only. Otherwise, access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserSID | Gets application groups with an associated user identified by their Windows SID.<br>If the 'UserFilterEnabled' property is true then access to applications in the application group is restricted to those users only. Otherwise, access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserUPN | Gets application groups with an associated user identified by their user principle name (in the form 'user@domain').<br>If the 'UserFilterEnabled' property is true then access to applications in the application group is restricted to those users only. Otherwise, access is unrestricted (but always subject to other policy rules). | false | false |  |
| Description | Gets application groups whose description matches the supplied pattern. | false | false |  |
| Enabled | Gets application groups which are currently enabled. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| RestrictToTag | Gets only application groups with the specified tag restriction. | false | false |  |
| ScopeId | Gets application groups which are part of the supplied administrative scope. The scope is identified by its GUID. | false | false |  |
| ScopeName | Gets application groups which are part of an administrative scope whose name matches the supplied pattern. | false | false |  |
| SessionSharingEnabled | Gets application groups for which session sharing is enabled. | false | false |  |
| SingleAppPerSession | Specifies whether each application launched from this application group starts in its own new session or can share an existing suitable session if present. | false | false |  |
| Tag | Gets application groups that have been tagged with a tag whose name matches the specified pattern. | false | false |  |
| TenantId | Gets desktop groups associated with the specified tenant identity. | false | false |  |
| TotalApplications | Gets application groups that contain the specified number of applications. | false | false |  |
| TotalMachines | Gets application groups that are published on the specified number of machines, without taking the tag restriction into account. | false | false |  |
| TotalMachinesWithTagRestriction | Gets application groups that are published on the specified number of machines, taking the tag restriction into account. | false | false |  |
| UserFilterEnabled | Gets application groups whose user filter is currently enabled. | false | false |  |
| UUID | Gets the application group with the given UUID. | false | false |  |
| ApplicationUid | Gets only application groups to which the given application has been added. | false | false |  |
| DesktopGroupUid | Gets application groups which have been added to the specified desktop group. | false | false |  |
| TagUid | Gets application groups that have been tagged the given tag. The tag is identified by its Uid. | false | false |  |
| UserSID | Gets application groups for which the specified user is a member of the user filter. The user account is identified by its SID. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Applicationgroup
Get-BrokerApplicationGroup returns an object for each matching application group.
## Notes
Application groups are explained in about\_Broker\_Applications.<br>    To perform greater-than or less-than comparisons, use -Filter. For more information, see about\_Broker\_Filtering and the examples.
## Examples

### Example 1
```
C:\PS> Get-BrokerApplicationGroup -Name "Account\*"
```
#### Description
Gets application groups whose name starts with "Account".
### Example 2
```
C:\PS> Get-BrokerApplicationGroup -SessionSharingEnabled $false
```
#### Description
Gets application groups for which session sharing with applications in other application groups has been disabled.
