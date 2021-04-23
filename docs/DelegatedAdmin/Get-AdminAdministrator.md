
# Get-Adminadministrator
Gets administrators configured for this site.
## Syntax
```
Get-AdminAdministrator [[-Name] <String>] [-Sid <String>] [-BuiltIn <Boolean>] [-Enabled <Boolean>] [-Metadata <String>] [-UserIdentity <String>] [-UserIdentityType <UserIdentityType>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves administrators matching the specified criteria. If no parameters are specified this cmdlet enumerates all administrators.

See about\_Admin\_Filtering for information about advanced filtering options.


## Related Commands

* [New-AdminAdministrator](./New-AdminAdministrator/)
* [Set-AdminAdministrator](./Set-AdminAdministrator/)
* [Remove-AdminAdministrator](./Remove-AdminAdministrator/)
* [Set-AdminAdministratorMetadata](./Set-AdminAdministratorMetadata/)
* [Remove-AdminAdministratorMetadata](./Remove-AdminAdministratorMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Gets administrators with the specified name. | false | true (ByValue, ByPropertyName) |  |
| Sid | Gets administrators with the specified SID (security identifier). | false | true (ByPropertyName) |  |
| BuiltIn | Gets administrators that are builtin | false | false |  |
| Enabled | Gets administrators with the specified value of Enabled. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| UserIdentity | Gets administrators with the specified UserIdentity (Windows security identifier or Citrix Cloud Identity). If the UserIdentityType is a Sid this will be the same as the Sid property. For Cloud administrators this will show cloud identity and the the Sid property will be null. | false | false |  |
| UserIdentityType | Gets administrators with the specified UserIdentityType (Windows security identifier or Citrix Cloud Identity). | false | false |  |
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

### Citrix.Delegatedadmin.Sdk.Administrator
Get-AdminAdministrator returns an object for each matching administrator.
## Examples

### Example 1
```
C:\PS> Get-AdminAdministrator -Name DOMAIN\TestUser
```
#### Description
Finds the administrator object (if one exists) for user "DOMAIN\\TestUser".
### Example 2
```
C:\PS> Get-AdminAdministrator -Enabled $false
```
#### Description
Finds all disabled administrator objects.
