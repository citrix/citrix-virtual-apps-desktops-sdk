
# Remove-Adminscope
Removes a scope from the site.
## Syntax
```
Remove-AdminScope [-InputObject] <Scope[]> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminScope [-Id] <Guid[]> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AdminScope [-Name] <String[]> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-AdminScope cmdlet deletes scopes from the site.

You cannot remove the built-in 'All' scope.

An error will be produced if the scope being removed is currently assigned to an administrator unless you specify the -Force option. When -Force is specified, any rights that reference the scope are also removed.


## Related Commands

* [New-AdminScope](./New-AdminScope/)
* [Get-AdminScope](./Get-AdminScope/)
* [Set-AdminScope](./Set-AdminScope/)
* [Rename-AdminScope](./Rename-AdminScope/)
* [Set-AdminScopeMetadata](./Set-AdminScopeMetadata/)
* [Remove-AdminScopeMetadata](./Remove-AdminScopeMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the scopes to remove (by scope object). | true | true (ByValue) |  |
| Id | Specifies the scopes to remove (by scope id). | true | true (ByPropertyName) |  |
| Name | Specifies the scopes to remove (by scope name). | true | true (ByPropertyName) |  |
| Force | Allow removal of scopes that are still in use. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Delegatedadmin.Sdk.Scope
You can pipe the scopes to be deleted into this command.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-AdminScope -Name Sales
```
#### Description
Remove the Sales scope.
### Example 2
```
C:\PS> Get-AdminScope -BuiltIn $false | Remove-AdminScope
```
#### Description
Attempt to remove all scopes (excluding the built-in 'All' scope). This fails if one of the scopes is assigned to an administrator.
