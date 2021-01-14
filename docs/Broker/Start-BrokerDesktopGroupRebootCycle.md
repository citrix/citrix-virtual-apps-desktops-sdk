
# Start-Brokerdesktopgrouprebootcycle
Creates and starts a reboot cycle for each specified desktop group.
## Syntax
```
Start-BrokerDesktopGroupRebootCycle [-InputObject] <DesktopGroup[]> -RebootDuration <Int32> [-RestrictToTagUid <Int32>] [-WarningDuration <Int32>] [-WarningTitle <String>] [-WarningMessage <String>] [-WarningRepeatInterval <Int32>] [-IgnoreMaintenanceMode <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Start-BrokerDesktopGroupRebootCycle cmdlet is used to create and start a reboot cycle for specified desktop groups.

The functionality offered is similar to that of New-BrokerRebootSchedule but the resulting reboot cycles execute once as defined by the command parameters rather than on a repeating schedule.


## Related Commands

* [Start-BrokerRebootCycle](./Start-BrokerRebootCycle/)
* [Stop-BrokerRebootCycle](./Stop-BrokerRebootCycle/)
* [Get-BrokerRebootCycle](./Get-BrokerRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Creates a reboot cycle for the specified desktop groups. Groups can be specified using UID values, name values (including wildcards) or desktop group SDK objects. | true | true (ByValue) |  |
| RebootDuration | Approximate maximum duration in minutes over which the reboot cycle runs. | true | false |  |
| RestrictToTagUid | If set to a Tag UID, only machines that have this tag will be rebooted. | false | false | null |
| WarningDuration | Time in minutes prior to a machine reboot at which a warning message is displayed in all user sessions on that machine. If the warning duration value is zero then no message is displayed. | false | false |  |
| WarningTitle | The window title used when showing the warning message in user sessions on a machine scheduled for reboot. | false | false |  |
| WarningMessage | Warning message displayed in user sessions on a machine scheduled for reboot. If the message is blank then no message is displayed. | false | false |  |
| WarningRepeatInterval | Number of minutes to wait before showing the reboot warning message again. | false | false |  |
| IgnoreMaintenanceMode | Option to reboot machines in maintenance mode. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Desktopgroup
Desktop groups may be specified through pipeline input. The groups can be specified using UID values, name values (including wildcards) or desktop group objects
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Get-BrokerDesktopGroup "SampleGroup" | Start-BrokerDesktopGroupRebootCycle -RebootDuration 240 -WarningMessage "Save your work" -WarningDuration 15 -RestrictToTagUid 2
```
#### Description
Starts a new reboot cycle for the desktop group called "SampleGroup". Each reboot cycle has a duration of six hours. Fifteen minutes prior to rebooting a machine, the message "Save your work" is displayed in each active user session. Only machines tagged with the tag having UID 2 will be rebooted.
