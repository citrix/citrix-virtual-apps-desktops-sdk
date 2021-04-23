
# Set-Configsite
Changes the overall settings of the site.
## Syntax
```
Set-ConfigSite [-SiteName <String>] [-ProductCode <String>] [-ProductEdition <String>] [-ProductVersion <String>] [-LicensingModel <String>] [-LicenseServerName <String>] [-LicenseServerPort <Int32>] [-LicenseServerUri <Uri>] [-PrimaryZone <Zone>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Set-ConfigSite cmdlet modifies properties of the site.

The site is a top-level, logical representation of the XenDesktop site, from the perspective of the configuration services running within the site.

A XenDesktop installation has only a single site instance.

Modifications to the product code, product edition, product version and licensing model properties are successful only if their values are consistent with the feature table. Use the Get-ConfigProduct, Get-ConfigProductEdition, Get-ConfigProductVersion and Get-ConfigLicensingModel cmdlets to determine consistent values.

To configure the site, first import the feature table using the Import-ConfigFeatureTable cmdlet.


## Related Commands

* [Export-ConfigFeatureTable](./Export-ConfigFeatureTable/)
* [Get-ConfigSite](./Get-ConfigSite/)
* [Get-ConfigProduct](./Get-ConfigProduct/)
* [Get-ConfigProductEdition](./Get-ConfigProductEdition/)
* [Get-ConfigProductFeature](./Get-ConfigProductFeature/)
* [Get-ConfigProductVersion](./Get-ConfigProductVersion/)
* [Get-ConfigLicensingModel](./Get-ConfigLicensingModel/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SiteName | Changes the name of the site. | false | false |  |
| ProductCode | Changes the product code.<br>The Get-ConfigProduct cmdlet returns a list of supported values. | false | false |  |
| ProductEdition | Changes the license edition. A license matching the specified edition must be available within the site's license server.<br>The Get-ConfigProductEdition returns a list of supported values. | false | false |  |
| ProductVersion | Changes the product version.<br>The Get-ConfigProductVersion returns a list of supported values. | false | false |  |
| LicensingModel | Changes the license model. A license matching the specified model must be available within the site's license server.<br>The Get-ConfigLicensingModel returns a list of supported values. | false | false |  |
| LicenseServerName | Changes the machine used by the brokering services to obtain licenses for desktop and application session brokering. The specified machine must be running a Citrix license server and have suitable licenses installed.<br>The license server machine can be specified by its DNS name ('machine.domain') or its numeric IP address. | false | false |  |
| LicenseServerPort | Changes the port number on the license server machine used by the brokering services to contact the Citrix license server. | false | false |  |
| LicenseServerUri | Changes the Uri of the web server for licensing. The hostname component of this Uri must match the Site's LicenseServerName property. | false | false |  |
| PrimaryZone | Changes the primary zone for the site.<br>Primary zone can be specified by Uid, Name or by passing a Zone object. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Site

## Examples

### Example 1
```
C:\PS> Set-ConfigSite -ProductEdition PLT
```
#### Description
Specifies the use of a Platinum edition license. A suitable license must be available on the site's license server.
