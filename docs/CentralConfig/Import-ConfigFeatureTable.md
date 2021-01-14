
# Import-Configfeaturetable
Sets the feature table of the site.
## Syntax
```
Import-ConfigFeatureTable [-Path] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Import-ConfigFeatureTable -Content <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description



## Related Commands

* [Export-ConfigFeatureTable](./Export-ConfigFeatureTable/)
* [Get-ConfigSite](./Get-ConfigSite/)
* [Set-ConfigSite](./Set-ConfigSite/)
* [Get-ConfigProduct](./Get-ConfigProduct/)
* [Get-ConfigProductEdition](./Get-ConfigProductEdition/)
* [Get-ConfigProductFeature](./Get-ConfigProductFeature/)
* [Get-ConfigProductVersion](./Get-ConfigProductVersion/)
* [Get-ConfigLicensingModel](./Get-ConfigLicensingModel/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Path | The path to the file containing the feature table | true | false |  |
| Content | Set the site's feature table. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1
```
C:\PS> Import-ConfigFeatureTable $xml
```
#### Description
Specifies the use of a Platinum edition license. A suitable license must be available on the site's license server.
