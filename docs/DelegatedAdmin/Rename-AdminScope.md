
# Rename-Adminscope
Rename a scope
## Syntax
```
Rename-AdminScope [-InputObject] <Scope> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Rename-AdminScope [-Id] <Guid> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Rename-AdminScope [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Rename-AdminScope cmdlet changes the name of a scope.

Scope names must be unique, and you cannot modify the name of the built-in 'All' scope.


## Related Commands

* [New-AdminScope](./New-AdminScope/)
* [Get-AdminScope](./Get-AdminScope/)
* [Set-AdminScope](./Set-AdminScope/)
* [Remove-AdminScope](./Remove-AdminScope/)
* [Set-AdminScopeMetadata](./Set-AdminScopeMetadata/)
* [Remove-AdminScopeMetadata](./Remove-AdminScopeMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the scope to rename (by object). | true | true (ByValue) |  |
| Id | Specifies the scope to rename (by id). | true | true (ByPropertyName) |  |
| Name | Specifies the scope to rename (by name). | true | true (ByPropertyName) |  |
| NewName | Specifies the new name of the scope. | true | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Delegatedadmin.Sdk.Scope
You can pipe the scope to be renamed into this command.
## Return Values

### None Or Citrix.Delegatedadmin.Sdk.Scope
When you use the PassThru parameter, Rename-AdminScope generates a Citrix.DelegatedAdmin.Sdk.Scope object. Otherwise, this cmdlet does not generate any output.
## Examples

### Example 1
```
C:\PS> Rename-AdminScope -Name Sales -NewName SalesDesktops
```
#### Description
Renames the 'Sales' scope to 'SalesDesktops'.
