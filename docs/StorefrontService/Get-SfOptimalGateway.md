
# Get-Sfoptimalgateway
Gets the configured optimal gateways for farms.
## Syntax
```
Get-SfOptimalGateway -SiteId <Int64> -ResourcesVirtualPath <String> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Gets the configured optimal gateways for farms.


## Related Commands

* [Set-SfOptimalGatewayCommand](./Set-SfOptimalGatewayCommand/)
* [Remove-SfOptimalGatewayCommand](./Remove-SfOptimalGatewayCommand/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SiteId | Site ID within IIS. This is typically 1 for the site in IIS where StoreFront is installed by default. | true | true (ByPropertyName) |  |
| ResourcesVirtualPath | Path to the store that is to be configured to have a farm to optimal gateway mapping.<br>Example: “/Citrix/Store” | true | true (ByPropertyName) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None

## Return Values

### Citrix.Storefront.Sdk.Optimalgateway

## Examples

### Example 1
```
C:\PS>Get-DSOptimalGatewayForFarms -siteId 1 -ResourcesVirtualPath "/Citrix/MyStore"
```
#### Description

