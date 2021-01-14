
# Set-Adminrole
Set the properties of a role.
## Syntax
```
Set-AdminRole [-InputObject] <Role[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-AdminRole [-Id] <Guid[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-AdminRole [-Name] <String[]> [-Description <String>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Set-AdminRole command allows the description of custom roles to be updated. You cannot modify built-in roles.

To modify the permissions of a role, use the Add-AdminPermission and Remove-AdminPermission cmdlets.

To update the metadata associated with a role, use the Set-AdminRoleMetadata and Remove-AdminRoleMetadata cmdlets.


## Related Commands

* [New-AdminRole](./New-AdminRole/)
* [Get-AdminRole](./Get-AdminRole/)
* [Remove-AdminRole](./Remove-AdminRole/)
* [Rename-AdminRole](./Rename-AdminRole/)
* [Set-AdminRoleMetadata](./Set-AdminRoleMetadata/)
* [Remove-AdminRoleMetadata](./Remove-AdminRoleMetadata/)
* [Add-AdminPermission](./Add-AdminPermission/)
* [Remove-AdminPermission](./Remove-AdminPermission/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the roles to update (by object). | true | true (ByValue) |  |
| Id | Specifies the roles to update (by id). | true | true (ByPropertyName) |  |
| Name | Specifies the roles to update (by name). | true | true (ByPropertyName) |  |
| Description | Supplies the new description value. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Delegatedadmin.Sdk.Role
You can pipe the roles to be updated into this command.
## Return Values

### None Or Citrix.Delegatedadmin.Sdk.Role
When you use the PassThru parameter, Set-AdminRole generates a Citrix.DelegatedAdmin.Sdk.Role object. Otherwise, this cmdlet does not generate any output.
## Examples

### Example 1
```
C:\PS> Set-AdminRole -Name Supervisor -Description "Helpdesk supervisor role"
```
#### Description
Change the description of the 'Supervisor' role.
