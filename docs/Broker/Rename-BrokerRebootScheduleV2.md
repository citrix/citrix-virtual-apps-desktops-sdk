
# Rename-Brokerrebootschedulev2
Renames a reboot schedule.
## Syntax
```
Rename-BrokerRebootScheduleV2 [-InputObject] <RebootScheduleV2[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Rename-BrokerRebootScheduleV2 [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Rename-BrokerRebootScheduleV2 cmdlet changes the name of a reboot schedule. A reboot schedule cannot have the same name as another reboot schedule.


## Related Commands

* [Get-BrokerRebootScheduleV2](./Get-BrokerRebootScheduleV2/)
* [Set-BrokerRebootScheduleV2](./Set-BrokerRebootScheduleV2/)
* [New-BrokerRebootScheduleV2](./New-BrokerRebootScheduleV2/)
* [Remove-BrokerRebootScheduleV2](./Remove-BrokerRebootScheduleV2/)
* [Stop-BrokerRebootCycle](./Stop-BrokerRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the reboot schedule to rename. | true | true (ByValue) | null |
| Name | Specifies the name of the reboot schedule to rename. | true | true (ByPropertyName) | null |
| NewName | Specifies the new name for the reboot schedule. | true | false | null |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Rebootschedulev2
You can pipe reboot schedules into Rename-BrokerRebootScheduleV2.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Rebootschedulev2
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.RebootScheduleV2 object.
## Examples

### Example 1
```
C:\PS> Rename-BrokerRebootScheduleV2 -Name "Old Name" -NewName "New Name"
```
#### Description
Renames the reboot schedule with name "Old Name" to "New Name".
### Example 2
```
C:\PS> Get-BrokerRebootScheduleV2 -Uid 1 | Rename-BrokerRebootScheduleV2 -NewName "New Name" -PassThru
```
#### Description
Renames reboot schedule with the Uid 1 to "New Name", showing the result.
