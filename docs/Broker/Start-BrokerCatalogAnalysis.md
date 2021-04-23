
# Start-Brokercataloganalysis
Performs a AppDNA analysis on catalog
## Syntax
```
Start-BrokerCatalogAnalysis [-InputObject] <Catalog[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Extracts OS metadata from a machine in the catalog and uploads it to AppDNA server


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the catalog to perform the analysis on. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Catalog
You can pipe in the catalogs on which to start the catalog analysis on.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Set-BrokerCatalogAnalysis -InputObject $obj-Uid
```
#### Description
This command starts a catalog analysis for the Catalog whose instance is pointed by \$obj-Uid
