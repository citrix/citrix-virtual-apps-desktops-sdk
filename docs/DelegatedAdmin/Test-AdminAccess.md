
# Test-Adminaccess
Retrieves the scopes where the specified operation is permitted.
## Syntax
```
Test-AdminAccess [-Operation] <String[]> [-Annotate] [-RejectedScopes] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet evaluates what rights the current user has, and from these determines the scopes where the specified operation is permitted.

Operations are the indivisible unit of functionality that each XenDesktop service can perform, and usually correspond to individual cmdlets.

If you specify the -Annotate option or specify multiple operations to check, the resulting object is annotated with the operation the result relates to.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Operation | The operation to query. | true | true (ByValue) |  |
| Annotate | Annotates each result with the operation it relates to. | false | false |  |
| RejectedScopes | Gets the scopes where operations are not allowed as well as the scopes where an operation is allowed | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Delegatedadmin.Sdk.Scopereference
The list of permissible scopes for the specified single operation.
### Psobject
The list of permissible scopes for each operation. This type of object is returned when the -Annotate option or multiple operations are specified.
## Notes
If the specified operation has unrestricted access a single object is returned representing the 'All' scope with a ScopeId of Guid.Empty (00000000-0000-0000-0000-000000000000).
## Examples

### Example 1
```
C:\PS> Test-AdminAccess -Operation 'Broker:GetCatalog'
```
#### Description
Queries the scopes where 'Broker:GetCatalog' is permitted.
### Example 2
```
C:\PS> Test-AdminAccess -Operation 'Broker:GetCatalog','Broker:GetMachine'
```
#### Description
Queries the scopes where 'Broker:GetCatalog' or 'Broker:GetMachine' are permitted.
