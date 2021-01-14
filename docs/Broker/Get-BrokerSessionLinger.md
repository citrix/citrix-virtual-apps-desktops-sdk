
# Get-Brokersessionlinger
Gets one or more session lingering settings.
## Syntax
```
Get-BrokerSessionLinger [-DesktopGroupUid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerSessionLinger [[-DesktopGroupName] <String>] [-AssociatedUserFullName <String>] [-AssociatedUserName <String>] [-AssociatedUserSID <String>] [-AssociatedUserUPN <String>] [-Enabled <Boolean>] [-MaxAverageLoadThreshold <Int32>] [-MaxLoadPerMachineThreshold <Int32>] [-MaxTimeBeforeDisconnect <TimeSpan>] [-MaxTimeBeforeTerminate <TimeSpan>] [-UserFilterEnabled <Boolean>] [-UserSID <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerSessionLinger cmdlet is used to enumerate desktop group session linger settings that match all of the supplied criteria.

Without parameters, Get-BrokerSessionLinger gets all the session linger settings that have been created. You can also use the parameters of Get-BrokerSessionLinger to filter the results to just the desktop group you're interested in.

Note that each desktop group can only have a single session linger setting. Session lingering only applies to application sessions.

See about\_Broker\_Filtering for information about advanced filtering options.


### Brokersessionlinger Object
The session linger object returned represents a session linger setting in a desktop group.


  * AssociatedUserFullNames (System.String\[\]) List of associated users (full names). Associated users is the list of users who are given access using the pre-launch/user mapping filter.

  * AssociatedUserNames (System.String\[\]) List of associated users (SAM names). Associated users is the list of users who are given access using the pre-launch/user mapping filter.

  * AssociatedUserSIDs (System.String\[\]) List of associated users (SIDs). Associated users is the list of users who are given access using the pre-launch/user mapping filter.

  * AssociatedUserUPNs (System.String\[\]) List of associated users (user principle names). Associated users is the list of users who are given access using the pre-launch/user mapping filter.

  * DesktopGroupName (System.String) Name of the associated desktop group.

  * DesktopGroupUid (System.Int32) Uid of the associated desktop group.

  * Enabled (System.Boolean) Specifies whether or not session lingering is enabled for the desktop group.

  * MaxAverageLoadThreshold (System.Int32) Specifies the average load threshold across the desktop group. After this threshold is hit lingering sessions will be terminated to reduce average load across the group. Sessions that have been lingering the longest will be chosen first.

  * MaxLoadPerMachineThreshold (System.Int32) Specifies the maximum load threshold per machine in the desktop group. After this threshold is hit lingering sessions on loaded machines will be terminated to reduce load. Sessions that have been lingering the longest will be chosen first.

  * MaxTimeBeforeDisconnect (System.TimeSpan) Specifies the maximum time by when a lingering session will be disconnected. The disconnect timer cannot be greater than the terminate timer. When the disconnect timer is same as the terminate timer, the session will be directly be terminated. The default value is 15 minutes. A value of 0 disables the disconnect timer.

  * MaxTimeBeforeTerminate (System.TimeSpan) Specifies the maximum time by when a lingering session will be terminated. When the disconnect timer is same as the terminate timer, the session will be directly be terminated. The default value is 8 hours. A value of 0 disables the terminate timer.

  * UserFilterEnabled (System.Boolean) Indicates if linger-specific user filter is enabled.


## Related Commands

* [New-BrokerSessionLinger](./New-BrokerSessionLinger/)
* [Set-BrokerSessionLinger](./Set-BrokerSessionLinger/)
* [Remove-BrokerSessionLinger](./Remove-BrokerSessionLinger/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DesktopGroupUid | Gets session linger setting that is associated with the specified desktop group Uid. | true | false |  |
| DesktopGroupName | Gets session linger setting that is associated with the specified desktop group name. | false | false |  |
| AssociatedUserFullName | Gets session linger settings with an associated user identified by their full name (usually 'first-name last-name'). If the 'UserFilterEnabled' property is true then access to the session linger is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserName | Gets session linger settings with an associated user identified by their user name (in the form 'domain\\user'). If the 'UserFilterEnabled' property is true then access to the session linger is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserSID | Gets session linger settings with an associated user identified by their Windows SID. If the 'UserFilterEnabled' property is true then access to the session linger is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |  |
| AssociatedUserUPN | Gets session linger settings with an associated user identified by their user principle name (in the form 'user@domain'). If the 'UserFilterEnabled' property is true then access to the session linger is restricted to those users only, otherwise access is unrestricted (but always subject to other policy rules). | false | false |  |
| Enabled | Gets only the session linger settings that have the specified value for whether the setting is enabled. | false | false |  |
| MaxAverageLoadThreshold | Gets only the session linger settings that have the specified average load threshold. | false | false |  |
| MaxLoadPerMachineThreshold | Gets only the session linger settings that have the specified maximum load threshold per machine. | false | false |  |
| MaxTimeBeforeDisconnect | Gets only the session linger settings that have the specified idle disconnect time. | false | false |  |
| MaxTimeBeforeTerminate | Gets only the session linger settings that have the specified idle terminate time. | false | false |  |
| UserFilterEnabled | Gets only session linger settings whose user filter is in the specified state. | false | false |  |
| UserSID | Gets only session linger settings with their accessibility restricted to include the specified user. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Sessionlinger
Get-BrokerSessionLinger returns an object for each session linger setting it gets.
## Examples

### Example 1
```
C:\PS> Get-BrokerSessionLinger -DesktopGroupName "test"
```
#### Description
Returns the session linger settings associated with the destkop group named 'test'.
