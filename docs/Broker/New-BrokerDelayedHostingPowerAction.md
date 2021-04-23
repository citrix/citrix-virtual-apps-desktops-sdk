
# New-Brokerdelayedhostingpoweraction
Causes a power action to be queued after a delay.
## Syntax
```
New-BrokerDelayedHostingPowerAction [-MachineName] <String> -Action <PowerManagementAction> -Delay <TimeSpan> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Causes a power action to be queued after the specified period of time.

Only ShutDown or Suspend actions can be requested to be delayed in this manner.

For a detailed description of the queuing mechanism, see 'help about\_Broker\_PowerManagement'.


## Related Commands

* [Get-BrokerDelayedHostingPowerAction](./Get-BrokerDelayedHostingPowerAction/)
* [New-BrokerDelayedHostingPowerAction](./New-BrokerDelayedHostingPowerAction/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| MachineName | Specifies the machine that the action is to be performed on.<br>The machine can be identified by DNS name, short name, SID, or name of the form domain\\machine. | true | true (ByPropertyName) |  |
| Action | Specifies the power state change action that is to be performed on the specified machine after the specified delay.<br>Valid values are Shutdown and Suspend. | true | true (ByPropertyName) |  |
| Delay | Specifies a timespan delay before the action is queued. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Delayedhostingpoweraction
New-BrokerDelayedHostingPowerAction returns the created delayed power action.
## Examples

### Example 1
```
C:\PS> New-BrokerDelayedHostingPowerAction -Action Shutdown -MachineName 'XD_VDA1' -Delay '00:02:00'
```
#### Description
Causes the machine called XD\_VDA1 to be shut down after a delay of two minutes.
