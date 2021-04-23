
# New-Brokerhostingpoweraction
Creates a new action in the power action queue.
## Syntax
```
New-BrokerHostingPowerAction [-MachineName] <String> -Action <PowerManagementAction> [-ActualPriority <Int32>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerHostingPowerAction cmdlet adds a new power action record into the queue of power actions to be performed. The power actions in the queue are processed on a priority basis and sent to the relevant hypervisor to change the power state of a virtual machine.

A power action record defines the action to be performed, the machine on which the action is to be performed, and an initial priority value for the action. Multiple actions may be created that relate to the same machine.

For a detailed description of the queuing mechanism, see 'help about\_Broker\_PowerManagement'.


## Related Commands

* [Get-BrokerHostingPowerAction](./Get-BrokerHostingPowerAction/)
* [Set-BrokerHostingPowerAction](./Set-BrokerHostingPowerAction/)
* [Remove-BrokerHostingPowerAction](./Remove-BrokerHostingPowerAction/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| MachineName | Specifies the machine that the action is to be performed on.<br>The machine can be identified by DNS name or short name or SID or 'machine\\domain' form name. | true | true (ByValue, ByPropertyName) |  |
| Action | Specifies the power state change action that is to be performed on the specified machine.<br>Valid values are: TurnOn, TurnOff, ShutDown, Reset, Restart, Suspend and Resume. | true | true (ByPropertyName) |  |
| ActualPriority | Specifies an initial priority value for the action in the queue.<br>This priority is the current action priority; the 'base' priority for actions created via this cmdlet is always 30. Numerically lower priority values indicate more important actions that are processed in preference to actions with numerically higher priority settings. | false | true (ByPropertyName) | 30 |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Machinename (System.String)
A list of machine names can be supplied as input.
## Return Values

### Citrix.Broker.Admin.Sdk.Hostingpoweraction
New-BrokerHostingPowerAction returns the newly created power action record.
## Examples

### Example 1
```
C:\PS> New-BrokerHostingPowerAction -Action Shutdown -MachineName 'XD_VDA1'
```
#### Description
Causes the machine called 'XD\_VDA1' to be shut down.
