
# Set-Brokerrebootschedule
Updates the values of one or more desktop group reboot schedules.
## Syntax
```
Set-BrokerRebootSchedule [-InputObject] <RebootSchedule[]> [-PassThru] [-Day <RebootScheduleDays>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-RebootDuration <Int32>] [-StartTime <TimeSpan>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerRebootSchedule [-DesktopGroupName] <String> [-PassThru] [-Day <RebootScheduleDays>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-RebootDuration <Int32>] [-StartTime <TimeSpan>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerRebootSchedule cmdlet is used to alter the settings of an existing desktop group reboot schedule.


## Related Commands

* [Get-BrokerRebootSchedule](./Get-BrokerRebootSchedule/)
* [New-BrokerRebootSchedule](./New-BrokerRebootSchedule/)
* [Remove-BrokerRebootSchedule](./Remove-BrokerRebootSchedule/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The reboot schedule to be modified. | true | true (ByValue) |  |
| DesktopGroupName | The name of the desktop group whose reboot schedule is to be modified. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Day | For weekly schedules, the day of the week on which the scheduled reboot-cycle starts (one of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday). | false | false |  |
| Enabled | Boolean that indicates if the reboot schedule is to be enabled or disabled. | false | false |  |
| Frequency | Frequency with which this schedule runs (either Weekly or Daily). | false | false |  |
| RebootDuration | Approximate maximum number of minutes over which the scheduled reboot cycle runs. | false | false |  |
| StartTime | Time of day at which the scheduled reboot cycle starts (HH:MM). | false | false |  |
| WarningDuration | Time prior to the initiation of a machine reboot at which warning message is displayed in all user sessions on that machine. If the warning duration is zero then no message is displayed. In some cases the time required to process a reboot schedule may exceed the RebootDuration time by up to the WarningDuration value; Citrix recommends that the WarningDuration is kept small relative to the RebootDuration value. | false | false |  |
| WarningMessage | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed. The optional pattern '%m%' is replaced by the number of minutes until the reboot. | false | false |  |
| WarningRepeatInterval | Time to wait after the previous reboot warning before displaying the warning message in all user sessions on that machine again. If the warning repeat interval is zero then the warning message is not displayed after the initial warning. | false | false |  |
| WarningTitle | The window title used when showing the warning message in user sessions on a machine scheduled for reboot. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Rebootschedule
Reboot schedules may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Set-BrokerRebootSchedule -DesktopGroupName Accounting -WarningMessage "Save your work" -WarningDuration 10 -WarningTitle "WARNING: Reboot pending"
```
#### Description
Sets the reboot schedule for the desktop group named Accounting to display a message with the title "WARNING: Reboot pending" and body "Save your work" ten minutes prior to rebooting each machine. The message is displayed in every user session on that machine.
### Example 2
```
C:\PS> Get-BrokerRebootSchedule -Frequency Weekly | Set-BrokerRebootSchedule -Day Friday
```
#### Description
Sets all weekly reboot schedules to run on Friday.
### Example 3
```
C:\PS> Set-BrokerRebootSchedule -DesktopGroupUid 17 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5
```
#### Description
Sets the reboot schedule for the desktop group having Uid 17 to display the message "Rebooting in %m% minutes." Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.
