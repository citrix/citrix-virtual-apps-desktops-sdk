
# Get-Configsite
Gets the site.
## Syntax
```
Get-ConfigSite [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Get-ConfigSite cmdlet gets the site.

A XenDesktop installation has only a single site instance.


## Related Commands

* [Set-ConfigSite](./Set-ConfigSite/)
* [Import-ConfigFeatureTable](./Import-ConfigFeatureTable/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Get-Configsite Returns The Site Instance.

## Examples

### Example 1
```
C:\PS> Get-ConfigSite
```
#### Description
Gets the site.
