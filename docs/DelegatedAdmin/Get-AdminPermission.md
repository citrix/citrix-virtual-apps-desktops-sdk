
# Get-Adminpermission
Gets permissions configured for the site.
## Syntax
```
Get-AdminPermission [[-Name] <String>] [-Id <String>] [-Description <String>] [-GroupId <String>] [-GroupName <String>] [-Metadata <String>] [-Operation <String>] [-ReadOnly <Boolean>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves permission matching the specified criteria. If no parameters are specified this cmdlet enumerates all permissions.

Permissions are configured using the Import-AdminRoleConfiguration command, and are used to represent collections of operations that are needed to perform a particular task. These permissions are presented in Citrix Studio when configuring roles.

Permissions can also have metadata associated with them.

See about\_Admin\_Filtering for information about advanced filtering options.


## Related Commands

* [Add-AdminPermission](./Add-AdminPermission/)
* [Remove-AdminPermission](./Remove-AdminPermission/)
* [Get-AdminRole](./Get-AdminRole/)
* [Get-AdminPermissionGroup](./Get-AdminPermissionGroup/)
* [Test-AdminAccess](./Test-AdminAccess/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Gets permissions with the specified name (localized) | false | true (ByValue, ByPropertyName) |  |
| Id | Gets permissions with the specified identifier. | false | true (ByPropertyName) |  |
| Description | Gets permissions with the specified description. | false | false |  |
| GroupId | Gets permissions that are a member of the specified permission group (by group id). | false | false |  |
| GroupName | Gets permissions that are a member of the specified permission group (by group name). | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Operation | Gets permissions that contain a specific operation. | false | false |  |
| ReadOnly | Gets permissions with the specified value for the ReadOnly flag. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Admin\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_Admin\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Delegatedadmin.Sdk.Permission
Get-AdminPermission returns an object for each matching permission.
## Examples

### Example 1
```
C:\PS> Get-AdminPermission -Name \*Edit\*
```
#### Description
Finds all permissions with 'Edit' in their names.
### Example 2
```
C:\PS> Get-AdminPermission -Operation "Broker:SetCatalog"

C:\PS> Get-AdminPermission -Filter { Operations -contains "Broker:SetCatalog" -or Operations -contains "Broker:NewCatalog" }
```
#### Description
Finds permissions that contain specific operations, with the -Filter form needed to match multiple values.
