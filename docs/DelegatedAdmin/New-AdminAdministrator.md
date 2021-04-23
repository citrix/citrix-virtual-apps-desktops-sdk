
# New-Adminadministrator
Adds a new administrator to the site.
## Syntax
```
New-AdminAdministrator [-Name] <String> [-Enabled <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AdminAdministrator -Sid <String> [-Enabled <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
New-AdminAdministrator creates a new administrator object in the site. Once a new administrator has been created you can assign rights (role and scope pairs) to the administrator.

Administrator objects are used to determine what rights, and therefore what permissions a particular Active Directory user has through the various SDKs and consoles of the site.

When the Enabled flag of an administrator is set to false, any rights of the administrator are ignored by the system when performing permission checks.


## Related Commands

* [Get-AdminAdministrator](./Get-AdminAdministrator/)
* [Set-AdminAdministrator](./Set-AdminAdministrator/)
* [Remove-AdminAdministrator](./Remove-AdminAdministrator/)
* [Set-AdminAdministratorMetadata](./Set-AdminAdministratorMetadata/)
* [Remove-AdminAdministratorMetadata](./Remove-AdminAdministratorMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the user or group name in Active Directory that this administrator corresponds to. | true | true (ByPropertyName) |  |
| Sid | Specifies the SID (security identifier) of the user in Active Directory that this administrator corresponds to. | true | true (ByPropertyName) |  |
| Enabled | Specifies whether the new administrator starts off enabled or not. | false | true (ByPropertyName) | True |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Delegatedadmin.Sdk.Administrator
The newly created administrator.
## Examples

### Example 1
```
C:\PS> New-AdminAdministrator -Name DOMAIN\TestUser
```
#### Description
Creates a new administrator object for user "DOMAIN\\TestUser". It defaults to enabled.
### Example 2
```
C:\PS> New-AdminAdministrator -Sid S-1-2-34-1234567890-1234567890-1234567890-123
```
#### Description
Creates a new administrator object for user with SID "S-1-2-34-1234567890-1234567890-1234567890-123". It defaults to enabled.
