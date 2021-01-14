
# Get-Configenabledfeature
Lists features of the site that are enabled.
## Syntax
```
Get-ConfigEnabledFeature [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description



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

### System.String

## Examples

### Example 1
```
C:\PS> Get-ConfigEnabledFeature
```
#### Description
Retrieves the list of enabled features for the site's current configuration.
