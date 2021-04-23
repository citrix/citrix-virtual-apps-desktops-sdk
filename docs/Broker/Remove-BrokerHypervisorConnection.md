
# Remove-Brokerhypervisorconnection
Removes a hypervisor connection from the system.
## Syntax
```
Remove-BrokerHypervisorConnection [-InputObject] <HypervisorConnection[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerHypervisorConnection [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Remove-BrokerHypervisorConnection removes a hypervisor connection from the system. A hypervisor connection cannot be removed if it's being used by a machine.


## Related Commands

* [Get-BrokerHypervisorConnection](./Get-BrokerHypervisorConnection/)
* [Set-BrokerHypervisorConnection](./Set-BrokerHypervisorConnection/)
* [New-BrokerHypervisorConnection](./New-BrokerHypervisorConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the hypervisor connection object to remove. | true | true (ByValue) |  |
| Name | Specifies the name of the hypervisor connection object to remove. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Hypervisorconnection
You can pipe the hypervisor connection to be removed to Remove-BrokerHypervisorConnection.
## Return Values

### None

## Examples

### Example 1
```
c:\PS> Remove-BrokerHypervisorConnection -Name "Xen Server Connection"
```
#### Description
This command removes a hypervisor connection by name.
### Example 2
```
c:\PS> $hvConn = Get-BrokerHypervisorConnection -PreferredController "controllerName" -Name "Xen Server Connection"

c:\PS> Remove-BrokerHypervisorConnection -InputObject $hvConn
```
#### Description
Gets a hypervisor connection by preferred controller and removes it.
