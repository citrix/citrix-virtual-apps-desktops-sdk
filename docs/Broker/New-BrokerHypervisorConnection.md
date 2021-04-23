
# New-Brokerhypervisorconnection
Creates a new hypervisor connection.
## Syntax
```
New-BrokerHypervisorConnection [-HypHypervisorConnectionUid] <Guid> [-PreferredController <String>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerHypervisorConnection cmdlet creates a new hypervisor connection.


## Related Commands

* [Get-BrokerHypervisorConnection](./Get-BrokerHypervisorConnection/)
* [Remove-BrokerHypervisorConnection](./Remove-BrokerHypervisorConnection/)
* [Set-BrokerHypervisorConnection](./Set-BrokerHypervisorConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| HypHypervisorConnectionUid | The Guid that identifies the hypervisor connection, as defined in DUM. | true | true (ByPropertyName) |  |
| PreferredController | The preferred controller machine for the hypervisor connection. Can be specified as (first match is used):<br>o Full SAM name.<br>o Full DNS name.<br>o SID value.<br>o NetBIOS name (SAM without domain).<br>o Partial DNS name (DNS name without some or all domain information).<br>Where not specified, the system selects preferred controller machine based on loading. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None

## Return Values

### Citrix.Broker.Admin.Sdk.Hypervisorconnection
New-BrokerHypervisorConnection returns an opaque object containing information about the hypervisor connection.
## Examples

### Example 1
```
C:\PS> New-BrokerHypervisorConnection -PreferredController "domainName\controllerName" -HypHypervisorConnectionUid "d16f4e56-b85e-4ba6-b745-0e978ae4f192"
```
#### Description
This command creates a new hypervisor connection with a preferred controller.
### Example 2
```
C:\PS> New-BrokerHypervisorConnection -HypHypervisorConnectionUid "d16f4e56-b85e-4ba6-b745-0e978ae4f192"
```
#### Description
This command creates a new hypervisor connection, and leaves it to the system to select a preferred controller.
