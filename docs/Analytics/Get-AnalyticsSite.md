
# Get-Analyticssite
This cmdlet returns the site configuration for the Analytics Service/Customer Experience Improvement Program. Details are available at http://more.citrix.com/XD-CEIP
## Syntax
```
Get-AnalyticsSite [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The configuration will be contained in the Site object that is returned. The Site object has two properties, Enabled, and DataDefinitionVersion. If Enabled is True, then site is participating in the Citrix Experience Improvement Program.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Analytics.Sdk.Site
The site object with configuration properties.
## Examples

### Example 1
```
c:\PS>Get-AnalyticsSite

          DataDefinitionVersion                           Enabled

          ---------------------                           -------

          1.0.0                                           False
```
#### Description
This retrieves the Analytics Site configuration.
