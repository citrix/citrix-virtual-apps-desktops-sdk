
# New-Adminscope
Adds a new scope to the site.
## Syntax
```
New-AdminScope [-Name] <String> [-Description <String>] [-TenantId <String>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
New-AdminScope adds a new scope object to the site.

A scope represents a collection of objects. Scopes are used to group objects in a way that is relevant to the organization; for example, the set of delivery groups used by the Sales team.

You can create objects in particular scopes by specifying the -Scope parameter of a New- cmdlet for an object that can be scoped. You can then modify the contents of a scope with Add-&lt;Noun&gt;Scope and Remove-&lt;Noun&gt;Scope cmdlets from the correpsonding PowerShell snap-ins.

To assign a scope to an administrator, combine it with a role and then assign this pair (also known as a 'right') to an administrator. See Add-AdminRight for further details.

The identifier of the new scope is chosen automatically.


## Related Commands

* [Get-AdminScope](./Get-AdminScope/)
* [Set-AdminScope](./Set-AdminScope/)
* [Rename-AdminScope](./Rename-AdminScope/)
* [Remove-AdminScope](./Remove-AdminScope/)
* [Set-AdminScopeMetadata](./Set-AdminScopeMetadata/)
* [Remove-AdminScopeMetadata](./Remove-AdminScopeMetadata/)
* [Add-AdminRight](./Add-AdminRight/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the name of the scope. Each scope in a site must have a unique name. | true | true (ByPropertyName) |  |
| Description | Specifies the description of the scope. | false | true (ByPropertyName) |  |
| TenantId | Specifies the tenant customer identifier of the scope. | false | true (ByPropertyName) | None |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Delegatedadmin.Sdk.Scope
The newly created scope.
## Examples

### Example 1
```
C:\PS> New-AdminScope -Name Sales -Description "Sales department scope"

C:\PS> Add-HypHypervisorConnectionScope -HypervisorConnectionName XenServer2 -Scope Sales

C:\PS> Add-AdminRight -Administrator DOMAIN\TestUser -Role Hosting -Scope Sales
```
#### Description
Creates a new scope called 'Sales', adds a hypervisor connection object to the scope, and then assigns the right to use the hosting role on the Sales scope to the 'TestUser' administrator.
