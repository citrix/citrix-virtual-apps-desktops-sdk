
# Rename-Brokercatalog
Renames a catalog.
## Syntax
```
Rename-BrokerCatalog [-InputObject] <Catalog[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Rename-BrokerCatalog [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Rename-BrokerCatalog cmdlet changes the name of a catalog. A catalog cannot have the same name as another catalog.

The following special characters are not allowed in a catalog name: \\ / ; : # . \* ? = &lt; &gt; | \[ \] ( ) " ' \`


## Related Commands

* [Get-BrokerCatalog](./Get-BrokerCatalog/)
* [New-BrokerCatalog](./New-BrokerCatalog/)
* [Remove-BrokerCatalog](./Remove-BrokerCatalog/)
* [Set-BrokerCatalog](./Set-BrokerCatalog/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the catalog to rename. | true | true (ByValue) |  |
| Name | Specifies the name of the catalog to rename. | true | true (ByPropertyName) |  |
| NewName | Specifies the new name of the catalog. | true | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Catalog
You can pipe catalogs to Rename-BrokerCatalog.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Catalog
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Catalog object.
## Examples

### Example 1
```
C:\PS> Rename-BrokerCatalog -Name "Old Name" -NewName "New Name"
```
#### Description
Renames the catalog with the name "Old Name" to "New Name".
### Example 2
```
C:\PS> c:\$catalog = Get-BrokerCatalog -Name "Old Name"

C:\PS> Rename-BrokerCatalog -InputObject $catalog -NewName "New Name"
```
#### Description
Renames the catalog with the name "Old Name" to "New Name".
