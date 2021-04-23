
# Set-Brokerrebootschedulev2
Updates the values of one or more desktop group reboot schedules.
## Syntax
```
Set-BrokerRebootScheduleV2 [-InputObject] <RebootScheduleV2[]> [-PassThru] [-Day <RebootScheduleDays>] [-Description <String>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-IgnoreMaintenanceMode <Boolean>] [-MaxOvertimeStartMins <Int32>] [-RebootDuration <Int32>] [-RestrictToTag <String>] [-StartTime <TimeSpan>] [-UseNaturalReboot <Boolean>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerRebootScheduleV2 [-Name] <String> [-PassThru] [-Day <RebootScheduleDays>] [-Description <String>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-IgnoreMaintenanceMode <Boolean>] [-MaxOvertimeStartMins <Int32>] [-RebootDuration <Int32>] [-RestrictToTag <String>] [-StartTime <TimeSpan>] [-UseNaturalReboot <Boolean>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerRebootScheduleV2 cmdlet is used to alter the settings of an existing desktop group reboot schedule.


## Related Commands

* [Get-BrokerRebootScheduleV2](./Get-BrokerRebootScheduleV2/)
* [New-BrokerRebootScheduleV2](./New-BrokerRebootScheduleV2/)
* [Remove-BrokerRebootScheduleV2](./Remove-BrokerRebootScheduleV2/)
* [Rename-BrokerRebootScheduleV2](./Rename-BrokerRebootScheduleV2/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The reboot schedule to be modified. | true | true (ByValue) |  |
| Name | The name of the reboot schedule | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Day | For weekly schedules, the day of the week on which the scheduled reboot-cycle starts (one of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday). | false | false |  |
| Description | An optional description for the reboot schedule. | false | false |  |
| Enabled | Boolean that indicates if the reboot schedule is to be enabled or disabled. | false | false |  |
| Frequency | Frequency with which this schedule runs (either Weekly or Daily). | false | false |  |
| IgnoreMaintenanceMode | Boolean value to reboot machines in maintenance mode | false | false |  |
| MaxOvertimeStartMins | Maximum delay in minutes after which the scheduled reboot will not take place | false | false |  |
| RebootDuration | Approximate maximum number of minutes over which the scheduled reboot cycle runs. | false | false |  |
| RestrictToTag | If specified, restricts the reboot schedule to only those machines in the desktop group with the specified tag. Specify \$null to remove any tag restriction. | false | false |  |
| StartTime | Time of day at which the scheduled reboot cycle starts (HH:MM). | false | false |  |
| UseNaturalReboot | Boolean value indicating whether the machines should reboot whenever they happen to have no sessions, rather than at equally spaced times within the cycle duration. | false | false |  |
| WarningDuration | Time prior to the initiation of a machine reboot at which warning message is displayed in all user sessions on that machine. If the warning duration is zero then no message is displayed. In some cases the time required to process a reboot schedule may exceed the RebootDuration time by up to the WarningDuration value; Citrix recommends that the WarningDuration is kept small relative to the RebootDuration value. | false | false |  |
| WarningMessage | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed. The optional pattern '%m%' is replaced by the number of minutes until the reboot. | false | false |  |
| WarningRepeatInterval | Time to wait after the previous reboot warning before displaying the warning message in all user sessions on that machine again. If the warning repeat interval is zero then the warning message is not displayed after the initial warning. | false | false |  |
| WarningTitle | The window title used when showing the warning message in user sessions on a machine scheduled for reboot. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Rebootschedulev2
Reboot schedules may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Set-BrokerRebootScheduleV2 -Name Accounting -WarningMessage "Save your work" -WarningDuration 10 -WarningTitle "WARNING: Reboot pending"
```
#### Description
Sets the reboot schedule for the reboot schedule named Accounting to display a message with the title "WARNING: Reboot pending" and body "Save your work" ten minutes prior to rebooting each machine. The message is displayed in every user session on that machine.
### Example 2
```
C:\PS> Get-BrokerRebootScheduleV2 -Frequency Weekly | Set-BrokerRebootScheduleV2 -Day Friday
```
#### Description
Sets all weekly reboot schedules to run on Friday.
### Example 3
```
C:\PS> Set-BrokerRebootScheduleV2 17 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5
```
#### Description
Sets the reboot schedule for the reboot schedule having Uid 17 to display the message "Rebooting in %m% minutes." Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.
### Example 4
```
C:\PS> Set-BrokerRebootScheduleV2 12 -RestrictToTag 'Finance Dept'
```
#### Description
Restricts the reboot schedule having uid 12 to only reboot machines within the desktop group tagged with the 'Finance Dept' tag.
