
# Remove-Adminadministrator
Removes administrators from the site.
## Syntax
```
Remove-AdminAdministrator [-InputObject] <Administrator[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminAdministrator -Sid <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminAdministrator [-Name] <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-AdminAdministrator cmdlet deletes administrators from the site.


## Related Commands

* [New-AdminAdministrator](./New-AdminAdministrator/)
* [Get-AdminAdministrator](./Get-AdminAdministrator/)
* [Set-AdminAdministrator](./Set-AdminAdministrator/)
* [Set-AdminAdministratorMetadata](./Set-AdminAdministratorMetadata/)
* [Remove-AdminAdministratorMetadata](./Remove-AdminAdministratorMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the administrators to delete. | true | true (ByValue) |  |
| Name | Specifies the name of the administrator to delete. | true | true (ByPropertyName) |  |
| Sid | Specifies the SID of the administrator to delete. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Delegatedadmin.Sdk.Administrator
You can pipe the adminstrators to be deleted into this command.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-AdminAdministrator DOMAIN\TestUser
```
#### Description
Remove the administrator called "DOMAIN\\TestUser".
### Example 2
```
C:\PS> Get-AdminAdministrator -Enabled $false | Remove-AdminAdministrator
```
#### Description
Remove all disabled administrators.
