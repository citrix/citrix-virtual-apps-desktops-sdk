
# Remove-Brokercatalog
Removes catalogs from the site.
## Syntax
```
Remove-BrokerCatalog [-InputObject] <Catalog[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerCatalog [-Name] <String> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Remove catalogs from the site.

In order to remove a catalog from a site, the catalog must not contain machines. To remove a machine from a catalog use the Remove-BrokerMachine cmdlet. Note: in order to remove a machine from a catalog, it must not belong to a desktop group.


## Related Commands

* [New-BrokerCatalog](./New-BrokerCatalog/)
* [Get-BrokerCatalog](./Get-BrokerCatalog/)
* [Rename-BrokerCatalog](./Rename-BrokerCatalog/)
* [Set-BrokerCatalog](./Set-BrokerCatalog/)
* [New-BrokerDesktopGroup](./New-BrokerDesktopGroup/)
* [Remove-BrokerDesktopGroup](./Remove-BrokerDesktopGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the catalog objects to delete. | true | true (ByValue) | null |
| Name | Specifies the name of the catalog to delete. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Catalog
You can pipe the catalogs to be deleted to Remove-BrokerCatalog.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerCatalog -Name "MyCatalog"

C:\PS> Remove-BrokerCatalog -InputObject (Get-BrokerCatalog -Name "MyCatalog")
```
#### Description
These commands delete the catalog with the name "MyCatalog".
### Example 2
```
C:\PS> Remove-BrokerCatalog -Name 'test\*'
```
#### Description
This command deletes all catalogs with names beginning with "test".
### Example 3
```
C:\PS> Get-BrokerCatalog -RemotePCDesktopGroupUid 42 | Remove-BrokerCatalog -RemotePCDesktopGroup 42
```
#### Description
Remove all the Remote PC catalogs that are associated with desktop group 42. Note that this only breaks the Remote PC relationships and does not delete the desktop groups.
