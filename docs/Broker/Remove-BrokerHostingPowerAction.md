
# Remove-Brokerhostingpoweraction
Cancel one or more pending power actions.
## Syntax
```
Remove-BrokerHostingPowerAction [-InputObject] <HostingPowerAction[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerHostingPowerAction [-MachineName] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Causes one or more of the pending power actions in the queue to be marked as canceled. The affected power actions are not sent to the hypervisor for processing, and take no further part in the queuing activity.

Power actions cannot be canceled once they have started to be processed by the hypervisor.


## Related Commands

* [Get-BrokerHostingPowerAction](./Get-BrokerHostingPowerAction/)
* [New-BrokerHostingPowerAction](./New-BrokerHostingPowerAction/)
* [Set-BrokerHostingPowerAction](./Set-BrokerHostingPowerAction/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The power action to be canceled. | true | true (ByValue) |  |
| MachineName | Cancels only actions for machines whose name (of the form domain\\machine) matches the specified string. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Hostingpoweraction
The power action to be canceled.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerHostingPowerAction -MachineName 'XD_VDA1'
```
#### Description
Cancels any pending power actions for the machine called 'XD\_VDA1'.
### Example 2
```
C:\PS> Get-BrokerHostingPowerAction -Filter { State -eq "Pending" -and RequestTime -gt "-00:05" } | Remove-BrokerHostingPowerAction
```
#### Description
Cancels any pending power actions requested in the last five minutes.
