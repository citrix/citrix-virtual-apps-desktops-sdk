
# Import-Adminroleconfiguration
Imports role configuration data into the Delegated Administration Service.
## Syntax
```
Import-AdminRoleConfiguration [-Path] <String> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Import-AdminRoleConfiguration -Content <String> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This command is intended for use by Citrix Studio to import definitions, roles, permissions, and their mappings to operations.

The supplied configuration requires a digital signature; this is used to validate the integrity of the configuration.


## Related Commands

* [Get-AdminRoleConfiguration](./Get-AdminRoleConfiguration/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Path | The path to the file containing the role configuration data. | true | false |  |
| Content | The content of the role configuration data. | true | true (ByValue) |  |
| Force | Allows older versions of role configuration to replace newer versions. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### None

## Notes
This command is supplied for infrastructure purposes only and is not intended for public use.
## Examples

### Example 1
```
C:\PS> Import-AdminRoleConfiguration -Path 'C:\MyAdminConfig.xml'
```
#### Description
Imports the contents of 'C:\\MyAdminConfig.xml' to the Delegated Administration Service.
