
# Get-Configproduct
Lists the site's supported product names and codes.
## Syntax
```
Get-ConfigProduct [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description



## Related Commands

* [Get-ConfigSite](./Get-ConfigSite/)
* [Set-ConfigSite](./Set-ConfigSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Psobject

## Examples

### Example 1
```
C:\PS> Get-ConfigProduct
```
#### Description
Lists the supported products by name and code.
