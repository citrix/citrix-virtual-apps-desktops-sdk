
# Get-Logsite
Gets global configuration logging settings.
## Syntax
```
Get-LogSite [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet retrieves the global configuration logging settings.


## Related Commands

* [Set-LogSite](./Set-LogSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Configurationlogging.Sdk.Site
Get-LogSite returns an object containing the following properties:<br>o Locale - the current language that logs should be recorded in. Can be: 'en', 'ja', 'zh-CN', 'de', 'es' or 'fr'.<br>o State - the current state of configuration logging. Can be: Enabled, Disabled, Mandatory or NotSupported.
## Examples

### Example 1
```
C:\PS> Get-LogSite
```
#### Description
Gets configiration logging site settings.
