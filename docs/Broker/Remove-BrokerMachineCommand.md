
# Remove-Brokermachinecommand
Cancel a pending command queued for delivery to a desktop.
## Syntax
```
Remove-BrokerMachineCommand [-InputObject] <MachineCommand[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Sets the state of a pending command queued for delivery to a desktop to Canceled. The command is not removed from the system.


## Related Commands

* [Get-BrokerMachineCommand](./Get-BrokerMachineCommand/)
* [New-BrokerMachineCommand](./New-BrokerMachineCommand/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Commands to cancel. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Machinecommand
Commands to cancel.
## Return Values

### None

## Examples

### Example 1
```
Get-BrokerMachineCommand | Remove-BrokerMachineCommand
```
#### Description
Cancel all pending commands.
### Example 2
```
Get-BrokerMachineCommand -Category "UPM" | Remove-BrokerMachineCommand
```
#### Description
Cancel all pending commands that have the category "UPM".
