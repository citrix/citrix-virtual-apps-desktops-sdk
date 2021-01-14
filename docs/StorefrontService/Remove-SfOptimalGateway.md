
# Remove-Sfoptimalgateway
Removes the optimal gateway for farms configuration.
## Syntax
```
Remove-SfOptimalGateway -SiteId <Int64> -ResourcesVirtualPath <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Removes the optimal gateway for farms configuration.


## Related Commands

* [Get-SfOptimalGatewayCommand](./Get-SfOptimalGatewayCommand/)
* [Set-SfOptimalGatewayCommand](./Set-SfOptimalGatewayCommand/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SiteId | Site ID within IIS. This is typically 1 for the site in IIS where StoreFront is installed by default. | true | true (ByPropertyName) |  |
| ResourcesVirtualPath | Path to the store that is to be configured to have a farm to optimal gateway mapping.<br>Example: “/Citrix/Store” | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None

## Return Values

### None

## Examples

### Example 1
```
C:\PS>Remove-DSOptimalGatewayForFarms -siteId 1 -ResourcesVirtualPath "/Citrix/MyStore"
```
#### Description

