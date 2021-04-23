
# New-Brokerrebootschedulev2
Creates a new reboot schedule for a desktop group.
## Syntax
```
New-BrokerRebootScheduleV2 [-Name] <String> -DesktopGroupName <String> -RebootDuration <Int32> [-Day <RebootScheduleDays>] [-Description <String>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-IgnoreMaintenanceMode <Boolean>] [-MaxOvertimeStartMins <Int32>] [-RestrictToTag <String>] [-StartTime <TimeSpan>] [-UseNaturalReboot <Boolean>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerRebootScheduleV2 [-Name] <String> -DesktopGroupUid <Int32> -RebootDuration <Int32> [-Day <RebootScheduleDays>] [-Description <String>] [-Enabled <Boolean>] [-Frequency <RebootScheduleFrequency>] [-IgnoreMaintenanceMode <Boolean>] [-MaxOvertimeStartMins <Int32>] [-RestrictToTag <String>] [-StartTime <TimeSpan>] [-UseNaturalReboot <Boolean>] [-WarningDuration <Int32>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-WarningTitle <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerRebootScheduleV2 cmdlet is used to define a reboot schedule for a desktop group.


## Related Commands

* [Get-BrokerRebootScheduleV2](./Get-BrokerRebootScheduleV2/)
* [Set-BrokerRebootScheduleV2](./Set-BrokerRebootScheduleV2/)
* [Remove-BrokerRebootScheduleV2](./Remove-BrokerRebootScheduleV2/)
* [Rename-BrokerRebootScheduleV2](./Rename-BrokerRebootScheduleV2/)
* [Start-BrokerRebootCycle](./Start-BrokerRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | The name of the new reboot schedule. | true | true (ByPropertyName) |  |
| RebootDuration | Approximate maximum number of minutes over which the scheduled reboot cycle runs. | true | true (ByPropertyName) |  |
| DesktopGroupName | The name of the desktop group that this reboot schedule is applied to. | true | true (ByPropertyName) |  |
| DesktopGroupUid | The Uid of the desktop group that this reboot schedule is applied to. | true | true (ByPropertyName) |  |
| Day | For weekly schedules, the day of the week on which the scheduled reboot-cycle starts (one of Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday). | false | true (ByPropertyName) |  |
| Description | An optional description for the reboot schedule. | false | true (ByPropertyName) |  |
| Enabled | Boolean that indicates if the new reboot schedule is enabled. | false | true (ByPropertyName) |  |
| Frequency | Frequency with which this schedule runs (either Weekly or Daily). | false | true (ByPropertyName) |  |
| IgnoreMaintenanceMode | Boolean value to reboot machines in maintenance mode | false | true (ByPropertyName) | false |
| MaxOvertimeStartMins | Maximum delay in minutes after which the scheduled reboot will not take place. | false | true (ByPropertyName) | 0 |
| RestrictToTag | If set the reboot schedule only applies to machines in the desktop group with the specified tag. | false | true (ByPropertyName) |  |
| StartTime | Time of day at which the scheduled reboot cycle starts (HH:MM). | false | true (ByPropertyName) |  |
| UseNaturalReboot | Boolean value indicating whether the machines should reboot whenever they happen to have no sessions, rather than at equally spaced times within the cycle duration. | false | true (ByPropertyName) | false |
| WarningDuration | Time prior to the initiation of a machine reboot at which warning message is displayed in all user sessions on that machine. If the warning duration is zero then no message is displayed. In some cases the time required to process a reboot schedule may exceed the RebootDuration time by up to the WarningDuration value; Citrix recommends that the WarningDuration is kept small relative to the RebootDuration value. | false | true (ByPropertyName) |  |
| WarningMessage | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed. The optional pattern '%m%' is replaced by the number of minutes until the reboot. | false | true (ByPropertyName) |  |
| WarningRepeatInterval | Time to wait after the previous reboot warning before displaying the warning message in all user sessions on that machine again. If the warning repeat interval is zero then the warning message is not displayed after the initial warning. | false | true (ByPropertyName) |  |
| WarningTitle | The window title used when showing the warning message in user sessions on a machine scheduled for reboot. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Rebootschedulev2

## Examples

### Example 1
```
C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "02:00" -Enabled $true -RebootDuration 120
```
#### Description
Schedules the machines in the desktop group named 'BankTellers' to be rebooted every night between 2 AM and 4 AM.
### Example 2
```
C:\PS> New-BrokerRebootScheduleV2 -Name 'Saturday reboots' -DesktopGroupUid 17 -Frequency Weekly -Day Saturday -StartTime "01:00" -Enabled $true -RebootDuration 240 -WarningTitle "WARNING: Reboot pending" -WarningMessage "Save your work" -WarningDuration 10
```
#### Description
Schedules the machines in the desktop group having Uid 17 to be rebooted every Saturday night between 1 AM and 5 AM. Ten minutes prior to rebooting, each machine will display a message box with the title "WARNING: Reboot pending" and message "Save your work" in every user session.
### Example 3
```
C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "03:00" -Enabled $true -RebootDuration 120 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5
```
#### Description
Schedules the machines in the desktop group named 'BankTellers' to be rebooted every night between 3 AM and 5 AM. Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.
### Example 4
```
C:\PS> New-BrokerRebootScheduleV2 -Name BankTellers-DailyReboot -DesktopGroupName BankTellers -Frequency Daily -StartTime "03:00" -Enabled $true -RebootDuration 120 -WarningMessage "Rebooting in %m% minutes." -WarningDuration 15 -WarningRepeatInterval 5 -RestrictToTag 'Daily Reboot'
```
#### Description
Schedules only machines with the tag 'Daily Reboot' in the desktop group named 'BankTellers' to be rebooted every night between 3 AM and 5 AM. Fifteen, ten and five minutes prior to rebooting each machine, the message "Rebooting in %m% minutes." will be displayed in each user session with the pattern '%m%' replaced with the number of minutes until the reboot.
