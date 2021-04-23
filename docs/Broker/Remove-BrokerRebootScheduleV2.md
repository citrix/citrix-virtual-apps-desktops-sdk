
# Remove-Brokerrebootschedulev2
Removes the reboot schedule.
## Syntax
```
Remove-BrokerRebootScheduleV2 [-InputObject] <RebootScheduleV2[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerRebootScheduleV2 [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerRebootScheduleV2 cmdlet is used to delete an existing reboot schedule.


## Related Commands

* [Get-BrokerRebootScheduleV2](./Get-BrokerRebootScheduleV2/)
* [Set-BrokerRebootScheduleV2](./Set-BrokerRebootScheduleV2/)
* [New-BrokerRebootScheduleV2](./New-BrokerRebootScheduleV2/)
* [Rename-BrokerRebootScheduleV2](./Rename-BrokerRebootScheduleV2/)
* [Stop-BrokerRebootCycle](./Stop-BrokerRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The reboot schedule to be removed. | true | true (ByValue) |  |
| Name | The name of the reboot schedule to be removed. | true | true (ByPropertyName) |  |
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
C:\PS> Get-BrokerRebootScheduleV2 | Remove-BrokerRebootScheduleV2
```
#### Description
Deletes every reboot schedule.
### Example 2
```
C:\PS> Remove-BrokerRebootScheduleV2 12
```
#### Description
Deletes the reboot schedule having Uid 12.
### Example 3
```
C:\PS> Remove-BrokerRebootScheduleV2 -Name Accounting
```
#### Description
Deletes the reboot schedule named Accounting.
