
# Remove-Brokerrebootschedule
Removes the reboot schedule.
## Syntax
```
Remove-BrokerRebootSchedule [-InputObject] <RebootSchedule[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerRebootSchedule [-DesktopGroupName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerRebootSchedule cmdlet is used to delete an existing reboot schedule.


## Related Commands

* [Get-BrokerRebootSchedule](./Get-BrokerRebootSchedule/)
* [Set-BrokerRebootSchedule](./Set-BrokerRebootSchedule/)
* [New-BrokerRebootSchedule](./New-BrokerRebootSchedule/)
* [Stop-BrokerRebootCycle](./Stop-BrokerRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The reboot schedule to be deleted. | true | true (ByValue) |  |
| DesktopGroupName | The name of the desktop group whose reboot schedule is to be removed. | true | true (ByPropertyName) |  |
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
C:\PS> Get-BrokerRebootSchedule | Remove-BrokerRebootSchedule
```
#### Description
Deletes every reboot schedule.
### Example 2
```
C:\PS> Remove-BrokerRebootSchedule 12
```
#### Description
Deletes the reboot schedule for the desktop group having Uid 12.
### Example 3
```
C:\PS> Remove-BrokerRebootSchedule -DesktopGroupName Accounting
```
#### Description
Deletes the reboot schedule for the desktop group named Accounting.
