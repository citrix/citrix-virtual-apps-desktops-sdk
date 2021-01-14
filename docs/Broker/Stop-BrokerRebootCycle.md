
# Stop-Brokerrebootcycle
Cancels the specified reboot cycle.
## Syntax
```
Stop-BrokerRebootCycle [-InputObject] <RebootCycle[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Stop-BrokerRebootCycle cmdlet is used to cancel the specified reboot cycle.


## Related Commands

* [Get-BrokerRebootCycle](./Get-BrokerRebootCycle/)
* [Start-BrokerRebootCycle](./Start-BrokerRebootCycle/)
* [Start-BrokerDesktopGroupRebootCycle](./Start-BrokerDesktopGroupRebootCycle/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Cancels this reboot cycle. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Rebootcycle
Reboot cycles may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Get-BrokerRebootCycle -CatalogUid 7 | Stop-BrokerRebootCycle
```
#### Description
Cancels every reboot cycle for the catalog that has the Uid of 7.
