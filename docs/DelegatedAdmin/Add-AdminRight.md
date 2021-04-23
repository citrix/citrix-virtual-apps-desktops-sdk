
# Add-Adminright
Grants a given right to the specified administrator.
## Syntax
```
Add-AdminRight -Scope <String> -Role <String> -Administrator <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Add-AdminRight -Role <String> -Administrator <String> [-All] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Add-AdminRight [-InputObject] <Right[]> -Administrator <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use the Add-AdminRight cmdlet to add rights (role and scope pairs) to an administrator.

For convenience, you can use the -All parameter to specify the 'All' scope.

Use the Get-AdminAdministrator cmdlet to determine what rights an administrator has.


## Related Commands

* [Get-AdminAdministrator](./Get-AdminAdministrator/)
* [Get-AdminEffectiveRight](./Get-AdminEffectiveRight/)
* [Remove-AdminRight](./Remove-AdminRight/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the rights to add from Right objects. | true | true (ByValue) |  |
| Scope | Specifies the scope name or scope identifier. | true | false |  |
| Role | Specifies the role name or role identifier. | true | false |  |
| Administrator | Specifies the name or ID of the administrator. | true | false |  |
| All | Specifies the 'All' scope. This parameter avoids localization issues or having to type the identifier of the 'All' scope. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Delegatedadmin.Sdk.Right
You can pipe the rights to be added into this command.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Add-AdminRight -Role 'Help Desk Administrator' -Scope London -Administrator DOMAIN\Admin1
```
#### Description
Assigns the 'Help Desk Administrator' role and 'London' scope to the 'Admin1' administrator.
### Example 2
```
C:\PS> Add-AdminRight -Role 'Full Administrator' -All -Administrator DOMAIN\Admin1
```
#### Description
Assigns the 'Full Administrator' role and 'All' scope to the 'Admin1' administrator.
### Example 3
```
C:\PS> $admin = Get-AdminAdministrator -Name DOMAIN\ExistingAdmin

C:\PS> Add-AdminRight -InputObject $admin.Rights -Administrator DOMAIN\NewAdmin
```
#### Description
Copies the administrator rights from 'ExistingAdmin' to 'NewAdmin'.
