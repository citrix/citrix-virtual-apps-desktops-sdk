
# Get-Brokerrebootschedulev2
Gets one or more reboot schedules.
## Syntax
```
Get-BrokerRebootScheduleV2 [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerRebootScheduleV2 [[-Name] <String>] [-Active <Boolean>] [-Day <RebootScheduleDays>] [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-IgnoreMaintenanceMode <Boolean>] [-MaxOvertimeStartMins <Int32>] [-MetadataKey <String>] [-Metadata <String>] [-RebootDuration <Int32>] [-RestrictToTag <String>] [-StartTime <TimeSpan>] [-UseNaturalReboot <Boolean>] [-WarningRepeatInterval <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerRebootScheduleV2 cmdlet is used to enumerate desktop group reboot schedules that match all of the supplied criteria.

A reboot schedule can be configured to cause all of the machines in a desktop group to be rebooted at a particular time each day or each week, with the reboot of the individual machines spread out over the duration of the whole reboot cycle. A specific warning message can be configured to be displayed to users who are running sessions on the machines being rebooted.

See about\_Broker\_Filtering for information about advanced filtering options.


### Brokerrebootschedulev2 Object
The reboot schedule object returned represents a regularly scheduled reboot of machines in a desktop group.


  * Active (System.Boolean) True if there is an active reboot cycle for this schedule, false otherwise.

  * Day (Citrix.Broker.Admin.SDK.RebootScheduleDays?) When the frequency is weekly, day of the week on which the schedule reboot starts.

  * Description (System.String) An optional description for the reboot schedule.

  * DesktopGroupName (System.String) Name of the desktop group rebooted by this schedule.

  * DesktopGroupUid (System.Int32) Uid of the desktop group rebooted by this schedule.

  * Enabled (System.Boolean) True if this schedule is currently enabled, false otherwise.

  * Frequency (Citrix.Broker.Admin.SDK.RebootScheduleFrequency) Whether the schedule runs daily or weekly.

  * IgnoreMaintenanceMode (System.Boolean) Boolean value to reboot machines in maintenance mode

  * MaxOvertimeStartMins (System.Int32) Maximum delay in minutes after which the scheduled reboot will not take place

  * MetadataKeys (System.String\[\]) All key names of metadata items associated with this application.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this application.

  * Name (System.String) Name of the reboot schedule.

  * RebootDuration (System.Int32) Approximate maximum number of minutes over which the scheduled reboot cycle runs.

  * RestrictToTag (System.String) If set the reboot schedule only applies to machines in the desktop group with the specified tag.

  * StartTime (System.TimeSpan) Time of day at which the scheduled reboot cycle starts.

  * Uid (System.Int32) Uid of the reboot schedule.

  * UseNaturalReboot (System.Boolean) Boolean value indicating whether the machines should reboot whenever they happen to have no sessions, rather than at equally spaced times within the cycle duration.

  * WarningDuration (System.Int32) Number of minutes to display the warning message for.

  * WarningMessage (System.String) Warning message to display to users in active sessions prior to rebooting the machine.

  * WarningRepeatInterval (System.Int32) Number of minutes to wait before displaying the warning message again.

  * WarningTitle (System.String) Title of the warning message dialog.


## Related Commands

* [Set-BrokerRebootScheduleV2](./Set-BrokerRebootScheduleV2/)
* [New-BrokerRebootScheduleV2](./New-BrokerRebootScheduleV2/)
* [Remove-BrokerRebootScheduleV2](./Remove-BrokerRebootScheduleV2/)
* [Rename-BrokerRebootScheduleV2](./Rename-BrokerRebootScheduleV2/)
* [Get-BrokerRebootCycle](./Get-BrokerRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the reboot schedule with the specified Uid. | true | false |  |
| Name | Gets the reboot schedule with the specified name. | false | false |  |
| Active | Gets desktop group reboot schedules according to whether they are currently active or not. A schedule is active if there is a reboot cycle currently running that was started as a result of the schedule. | false | false |  |
| Day | Gets the reboot schedules set to run on the specified day (one of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday). | false | false |  |
| DesktopGroupName | Gets the reboot schedules for the desktop group having this name. | false | false |  |
| DesktopGroupUid | Gets the reboot schedules for the desktop group having this Uid. | false | false |  |
| Enabled | Gets the reboot schedules with the specified Enabled value. | false | false |  |
| Frequency | Gets the reboot schedules with the specified frequency (either Weekly or Daily). | false | false |  |
| IgnoreMaintenanceMode | Boolean value to reboot machines in maintenance mode | false | false |  |
| MaxOvertimeStartMins | Maximum delay in minutes after which the scheduled reboot will not take place | false | false |  |
| MetadataKey | All key names of metadata items associated with this application. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| RebootDuration | Gets the reboot schedules with the specified duration. | false | false |  |
| RestrictToTag | Gets the reboot schedules with the specified tag. | false | false |  |
| StartTime | Gets the reboot schedules with the specified start time (HH:MM). | false | false |  |
| UseNaturalReboot | Gets the reboot schedules with the specified UseNaturalReboot value. | false | false |  |
| WarningRepeatInterval | Gets the reboot schedules with the specified warning repeat interval. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Rebootschedulev2
Returns matching reboot schedules.
## Examples

### Example 1
```
C:\PS> Get-BrokerRebootScheduleV2
```
#### Description
Enumerates all of the reboot schedules.
### Example 2
```
C:\PS> Get-BrokerRebootScheduleV2 -Enabled $false -Frequency Daily
```
#### Description
Enumerates all disabled reboot schedules that are scheduled to run daily.
### Example 3
```
C:\PS> Get-BrokerRebootScheduleV2 -DesktopGroupUid 11
```
#### Description
Returns the reboot schedules for the desktop group having the Uid 11.
