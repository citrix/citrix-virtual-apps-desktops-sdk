
# Set-Brokermachinecatalog
Moves one or more machines into a different catalog.
## Syntax
```
Set-BrokerMachineCatalog [-InputObject] <Machine[]> [-CatalogUid] <Int32> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerMachineCatalog cmdlet is used to move machines into a different catalog. The following properties of the destination catalog must exactly match those of the machine's current catalog otherwise the command fails:


* AllocationType
* ProvisioningType
* PersistUserChanges
* SessionSupport
* IsRemotePC
* MinimumFunctionalLevel
* PhysicalMachines

Changing a machine's catalog does not change the machine's desktop group membership. There is no effect on user sessions present on a machine if its catalog is changed.


## Related Commands

* [Set-BrokerMachine](./Set-BrokerMachine/)
* [New-BrokerCatalog](./New-BrokerCatalog/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The machine instances that are being moved into a different catalog. | true | true (ByValue) |  |
| CatalogUid | The unique identifier of the catalog into which the machines are being moved. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Machine
You can pipe in the machines that are to be moved into a new catalog.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> $catalog = Get-BrokerCatalog MarketingMachines

          C:\PS> $machines = Get-BrokerMachine -MachineName 'Marketing\\*'

          C:\PS> Set-BrokerMachineCatalog $machines -CatalogUid $cat.Uid
```
#### Description
This example finds all machines in domain Marketing and moves them into a catalog called MarketingMachines.
