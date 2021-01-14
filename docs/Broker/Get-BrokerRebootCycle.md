
# Get-Brokerrebootcycle
Gets one or more reboot cycles.
## Syntax
```
Get-BrokerRebootCycle -Uid <Int64> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerRebootCycle [-CatalogName <String>] [-CatalogUid <Int32>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-EndTime <DateTime>] [-IgnoreMaintenanceMode <Boolean>] [-MachinesCompleted <Int32>] [-MachinesFailed <Int32>] [-MachinesInProgress <Int32>] [-MachinesPending <Int32>] [-MachinesSkipped <Int32>] [-Metadata <String>] [-RebootDuration <Int32>] [-RebootScheduleName <String>] [-RebootScheduleUid <Int32>] [-RestrictToTag <String>] [-StartTime <DateTime>] [-State <RebootCycleState>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerRebootCycle cmdlet is used to enumerate reboot cycles that match all of the supplied criteria.

See about\_Broker\_Filtering for information about advanced filtering options.


### Brokerrebootcycle Object
The reboot cycle object returned represents a single occurrence of the process of rebooting a portion (or all) of the machines in a desktop group.


  * CatalogName (System.String) Name of the catalog whose machines are rebooted by this cycle if the cycle is associated with a catalog.

  * CatalogUid (System.Int32?) Uid of the catalog whose machines are rebooted by this cycle if the cycle is associated with a catalog.

  * DesktopGroupName (System.String) Name of the desktop group whose machines are rebooted by this cycle.

  * DesktopGroupUid (System.Int32) Uid of the desktop group whose machines are rebooted by this cycle.

  * EndTime (System.DateTime?) Time at which this cycle was completed, canceled or abandoned.

  * IgnoreMaintenanceMode (System.Boolean) Boolean value to optionally reboot machines in maintenance mode

  * MachinesCompleted (System.Int32) Number of machines successfully rebooted by this cycle.

  * MachinesFailed (System.Int32) Number of machines issued with reboot requests where either the request failed or the operation did not complete within the allowed time.

  * MachinesInProgress (System.Int32) Number of machines issued with reboot requests but which have not yet completed the operation.

  * MachinesPending (System.Int32) Number of outstanding machines to be rebooted during the cycle but on which processing has not yet started.

  * MachinesSkipped (System.Int32) Number of machines scheduled for reboot during the cycle but which were not processed either because the cycle was canceled or abandoned or because the machine was unavailable for reboot processing throughout the cycle.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Map of metadata associated with this cycle.

  * RebootDuration (System.Int32) Approximate maximum number of minutes over which the reboot cycle runs.

  * RebootScheduleName (System.String) Name of the Reboot Schedule which triggered this cycle if the cycle is associated with a reboot schedule.

  * RebootScheduleUid (System.Int32?) Uid of the Reboot Schedule which triggered this cycle if the cycle is associated with a reboot schedule.

  * RestrictToTag (System.String) An optional Tag which limits the reboot cycle to machines within the desktop group with the specified tag.

  * StartTime (System.DateTime) Time of day at which this reboot cycle was started.

  * State (Citrix.Broker.Admin.SDK.RebootCycleState) The execution state of this cycle.

  * Uid (System.Int64) Unique ID of this reboot cycle.

  * WarningDuration (System.Int32) Number of minutes to display the warning message for.

  * WarningMessage (System.String) Warning message to display to users in active sessions prior to rebooting the machine.

  * WarningRepeatInterval (System.Int32) Number of minutes to wait before showing the reboot warning message again.

  * WarningTitle (System.String) Title of the warning message dialog.


## Related Commands

* [Start-BrokerRebootCycle](./Start-BrokerRebootCycle/)
* [Start-DesktopGroupRebootCycle](./Start-DesktopGroupRebootCycle/)
* [Stop-BrokerRebootCycle](./Stop-BrokerRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets reboot cycles that have the specified Uid. | true | false |  |
| CatalogName | Gets reboot cycles that relate to the named catalog. | false | false |  |
| CatalogUid | Gets reboot cycles that relate to the catalog with a particular Uid. | false | false |  |
| DesktopGroupName | Gets reboot cycles that relate to the named desktop group. | false | false |  |
| DesktopGroupUid | Gets reboot cycles that relate to the desktop group with a particular Uid. | false | false |  |
| EndTime | Gets reboot cycles that have the specified time at which the reboot cycle was completed, canceled or abandoned. | false | false |  |
| IgnoreMaintenanceMode | Boolean value to optionally reboot machines in maintenance mode | false | false |  |
| MachinesCompleted | Gets reboot cycles that have the specified count of machines successfully rebooted during the cycle. | false | false |  |
| MachinesFailed | Gets reboot cycles that have the specified count of machines issued with reboot requests where either the request failed or the operation did not complete within the allowed time. | false | false |  |
| MachinesInProgress | Gets reboot cycles that have the specified count of machines issued with reboot requests but which have not yet completed the operation. | false | false |  |
| MachinesPending | Gets reboot cycles that have the specified count of outstanding machines to be rebooted during the cycle but on which processing has not yet started. | false | false |  |
| MachinesSkipped | Gets reboot cycles that have the specified count of machines scheduled for reboot during the cycle but which were not processed either because the cycle was canceled or abandoned or because the machine was unavailable for reboot processing throughout the cycle. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| RebootDuration | Gets reboot cycles that have the specified approximate maximum duration in minutes over which the reboot cycle runs. | false | false |  |
| RebootScheduleName | Gets reboot cycles which were triggered by the named reboot schedule. | false | false |  |
| RebootScheduleUid | Gets reboot cycles which were triggered by the reboot schedule with aparticular Uid. | false | false |  |
| RestrictToTag | An optional Tag which limits the reboot cycle to machines within the desktop group with the specified tag. | false | false |  |
| StartTime | Gets reboot cycles that have the specified time at which the reboot cycle started. | false | false |  |
| State | Gets reboot cycles that have the specified overall state of the reboot cycle. Valid values are Initializing, Active, Completed, Canceled, and Abandoned. | false | false |  |
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
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Rebootcycle
Returns matching reboot cycles.
## Examples

### Example 1
```
C:\PS> Get-BrokerRebootCycle
```
#### Description
Enumerate all reboot cycles.
### Example 2
```
C:\PS> Get-BrokerRebootCycle -State Completed
```
#### Description
Enumerates all reboot cycles that have successfully completed.
### Example 3
```
C:\PS> Get-BrokerRebootCycle -DesktopGroupName CallCenter
```
#### Description
Enumerates all reboot cycles related to the desktop group named CallCenter.
