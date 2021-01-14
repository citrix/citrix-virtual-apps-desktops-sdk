
# Set-Adminscope
Set the properties of a scope.
## Syntax
```
Set-AdminScope [-InputObject] <Scope[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-AdminScope [-Id] <Guid[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-AdminScope [-Name] <String[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Set-AdminScope command allows the description of scopes to be updated. You cannot modify the built-in 'All' scope.

To change the contents of a scope, use the Add-&lt;Noun&gt;Scope and Remove-&lt;Noun&gt;Scope cmdlets from the corresponding PowerShell snap-in.

To update the metadata associated with a scope, use the Set-AdminScopeMetadata and Remove-AdminScopeMetadata cmdlets.


## Related Commands

* [New-AdminScope](./New-AdminScope/)
* [Get-AdminScope](./Get-AdminScope/)
* [Remove-AdminScope](./Remove-AdminScope/)
* [Rename-AdminScope](./Rename-AdminScope/)
* [Set-AdminScopeMetadata](./Set-AdminScopeMetadata/)
* [Remove-AdminScopeMetadata](./Remove-AdminScopeMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the scopes to update (by object). | true | true (ByValue) |  |
| Id | Specifies the scopes to update (by id). | true | true (ByPropertyName) |  |
| Name | Specifies the scopes to update (by name). | true | true (ByPropertyName) |  |
| Description | Supplies the new description value. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Delegatedadmin.Sdk.Scope
You can pipe the scopes to be updated into this command.
## Return Values

### None Or Citrix.Delegatedadmin.Sdk.Scope
When you use the PassThru parameter, Set-AdminScope generates a Citrix.DelegatedAdmin.Sdk.Scope object. Otherwise, this cmdlet does not generate any output.
## Examples

### Example 1
```
C:\PS> Set-AdminScope -Name Sales -Description "Sales department desktops"
```
#### Description
Change the description of the 'Sales' scope.
