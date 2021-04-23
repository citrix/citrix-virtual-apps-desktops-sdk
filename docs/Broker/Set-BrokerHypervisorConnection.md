
# Set-Brokerhypervisorconnection
Sets the properties of a hypervisor connection.
## Syntax
```
Set-BrokerHypervisorConnection [-InputObject] <HypervisorConnection[]> [-PassThru] [-PreferredController <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerHypervisorConnection [-Name] <String> [-PassThru] [-PreferredController <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerHypervisorConnection cmdlet sets the properties on a hypervisor connection.


## Related Commands

* [Get-BrokerHypervisorConnection](./Get-BrokerHypervisorConnection/)
* [New-BrokerHypervisorConnection](./New-BrokerHypervisorConnection/)
* [Remove-BrokerHypervisorConnection](./Remove-BrokerHypervisorConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the hypervisor connection object to adjust. | true | true (ByValue) |  |
| Name | Specifies the name of the hypervisor connection object to adjust. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| PreferredController | Supplies the new value of the PreferredController property. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Hypervisorconnection
You can pipe the hypervisor connection to be modified to Set-BrokerHypervisorConnection.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Hypervisorconnection
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.HypervisorConnection object.
## Examples

### Example 1
```
c:\PS> $hvConn = Get-BrokerHypervisorConnection -PreferredController "oldController" -Name "Xen Server Connection"

c:\PS> Set-BrokerHypervisorConnection -InputObject $hvConn -PreferredController "newController"
```
#### Description
Updates the preferred controller for a hypervisor connection.
