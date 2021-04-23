
# Remove-Acctidentitypoolscope
Remove the specified IdentityPool(s) from the given scope(s).
## Syntax
```
Remove-AcctIdentityPoolScope [-Scope] <String[]> -InputObject <IdentityPool[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AcctIdentityPoolScope [-Scope] <String[]> -IdentityPoolUid <Guid[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AcctIdentityPoolScope [-Scope] <String[]> -IdentityPoolName <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-AcctIdentityPoolScope command is used to remove one or more IdentityPool objects from the given scope(s).

There are multiple parameter sets for this cmdlet, allowing you to identify the IdentityPool objects in different ways: - IdentityPool objects can be piped in or specified by the InputObject parameter - The IdentityPoolUid parameter specifies objects by IdentityPoolUid - The IdentityPoolName parameter specifies objects by IdentityPoolName (supports wildcards)

To remove a IdentityPool from a scope you need permission to change the scopes of the IdentityPool.

If the IdentityPool is not in a specified scope, that scope will be silently ignored.


## Related Commands

* [Add-AcctIdentityPoolScope](./Add-AcctIdentityPoolScope/)
* [Get-AcctScopedObject](./Get-AcctScopedObject/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Scope | Specifies the scopes to remove the objects from. | true | false |  |
| InputObject | Specifies the IdentityPool objects to be removed. | true | true (ByValue, ByPropertyName) |  |
| IdentityPoolUid | Specifies the IdentityPool objects to be removed by IdentityPoolUid. | true | true (ByValue, ByPropertyName) |  |
| IdentityPoolName | Specifies the IdentityPool objects to be removed by IdentityPoolName. | true | true (ByValue, ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### None

## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        One of the specified objects was not found.<br>    ScopeNotFound<br>        One of the specified scopes was not found.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command with the specified objects or scopes.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Remove-AcctIdentityPoolScope Finance -IdentityPoolUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
```
#### Description
Removes a single IdentityPool from the 'Finance' scope.
### Example 2
```
c:\PS>Remove-AcctIdentityPoolScope Finance,Marketing -IdentityPoolUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
```
#### Description
Removes a single IdentityPool from multiple scopes.
### Example 3
```
c:\PS>Get-AcctIdentityPool | Remove-AcctIdentityPoolScope Finance
```
#### Description
Removes all visible IdentityPool objects from the 'Finance' scope.
### Example 4
```
c:\PS>Remove-AcctIdentityPoolScope Finance -IdentityPoolName A\*
```
#### Description
Removes IdentityPool objects with a name starting with an 'A' from the 'Finance' scope.
