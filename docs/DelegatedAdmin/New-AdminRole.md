
# New-Adminrole
Adds a new custom role to the site.
## Syntax
```
New-AdminRole [-Name] <String> [-Description <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
New-AdminRole adds a new custom role object to the site. Once a new role has been created, you can add permissions to the role which define what operations the role conveys.

Roles represent a job function, such as 'help desk administrator', and contain a list of permissions that are required to perform that job function.

To assign a role to an administrator, you combine it with a scope which indicates what objects the role can operate on. This pair (also known as a 'right') can then be assigned to an administrator. See Add-AdminRight for further details.

The identifier of the new role is chosen automatically, and custom roles created with this cmdlet always have their BuiltIn flag set to false.

You cannot modify built-in roles, and only some license editions support custom roles.


## Related Commands

* [Get-AdminRole](./Get-AdminRole/)
* [Set-AdminRole](./Set-AdminRole/)
* [Rename-AdminRole](./Rename-AdminRole/)
* [Remove-AdminRole](./Remove-AdminRole/)
* [Set-AdminRoleMetadata](./Set-AdminRoleMetadata/)
* [Remove-AdminRoleMetadata](./Remove-AdminRoleMetadata/)
* [Add-AdminPermission](./Add-AdminPermission/)
* [Add-AdminRight](./Add-AdminRight/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the name of the role. Each role in a site must have a unique name. | true | true (ByPropertyName) |  |
| Description | Specifies the description of the role. | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Delegatedadmin.Sdk.Role
The newly created role.
## Notes
Roles are created without any permissions. Use the Add-AdminPermission to add permissions.
## Examples

### Example 1
```
C:\PS> New-AdminRole -Name Supervisor -Description "My custom supervisor role"

C:\PS> $list = Get-AdminRole 'Help Desk Administrator' | Select -Expand Permissions

C:\PS> Add-AdminPermission -Role Supervisor -Permission $list

C:\PS> Add-AdminPermission -Role Supervisor -Permission $extras

C:\PS> Add-AdminRight -Administrator DOMAIN\TestUser -Role Supervisor -All
```
#### Description
Creates a new role called 'Supervisor', and then copies the permissions from the help desk role and adds some extras. Then gives this role (with the all scope) to user 'TestUser'.
