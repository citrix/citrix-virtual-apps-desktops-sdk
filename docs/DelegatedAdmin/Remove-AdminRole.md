
# Remove-Adminrole
Removes a role from the site.
## Syntax
```
Remove-AdminRole [-InputObject] <Role[]> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminRole [-Id] <Guid[]> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminRole [-Name] <String[]> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-AdminRole cmdlet deletes roles from the site.

You cannot remove built-in roles.

An error will be produced if the role being removed is currently assigned to an administrator unless you specify the -Force option. When -Force is specified, any rights that reference the role are also removed.


## Related Commands

* [New-AdminRole](./New-AdminRole/)
* [Get-AdminRole](./Get-AdminRole/)
* [Set-AdminRole](./Set-AdminRole/)
* [Rename-AdminRole](./Rename-AdminRole/)
* [Set-AdminRoleMetadata](./Set-AdminRoleMetadata/)
* [Remove-AdminRoleMetadata](./Remove-AdminRoleMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the roles to remove (by role object). | true | true (ByValue) |  |
| Id | Specifies the roles to remove (by role id). | true | true (ByPropertyName) |  |
| Name | Specifies the roles to remove (by role name). | true | true (ByPropertyName) |  |
| Force | Allow removal of roles that are still in use. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Delegatedadmin.Sdk.Role
You can pipe the roles to be deleted into this command.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-AdminRole -Name Supervisor
```
#### Description
Remove the Supervisor role.
### Example 2
```
C:\PS> Get-AdminRole -BuiltIn $false | Remove-AdminRole
```
#### Description
Attempt to remove all custom roles. This fails if one of the roles is assigned to an administrator.
