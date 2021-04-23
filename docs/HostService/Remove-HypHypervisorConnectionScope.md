
# Remove-Hyphypervisorconnectionscope
Remove the specified HypervisorConnection(s) from the given scope(s).
## Syntax
```
Remove-HypHypervisorConnectionScope [-Scope] <String[]> -InputObject <HypervisorConnection[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-HypHypervisorConnectionScope [-Scope] <String[]> -HypervisorConnectionUid <Guid[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-HypHypervisorConnectionScope [-Scope] <String[]> -HypervisorConnectionName <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-HypHypervisorConnectionScope command is used to remove one or more HypervisorConnection objects from the given scope(s).

There are multiple parameter sets for this cmdlet, allowing you to identify the HypervisorConnection objects in different ways: - HypervisorConnection objects can be piped in or specified by the InputObject parameter - The HypervisorConnectionUid parameter specifies objects by HypervisorConnectionUid - The HypervisorConnectionName parameter specifies objects by HypervisorConnectionName (supports wildcards)

To remove a HypervisorConnection from a scope you need permission to change the scopes of the HypervisorConnection.

If the HypervisorConnection is not in a specified scope, that scope will be silently ignored.


## Related Commands

* [Add-HypHypervisorConnectionScope](./Add-HypHypervisorConnectionScope/)
* [Get-HypScopedObject](./Get-HypScopedObject/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Scope | Specifies the scopes to remove the objects from. | true | false |  |
| InputObject | Specifies the HypervisorConnection objects to be removed. | true | true (ByValue, ByPropertyName) |  |
| HypervisorConnectionUid | Specifies the HypervisorConnection objects to be removed by HypervisorConnectionUid. | true | true (ByValue, ByPropertyName) |  |
| HypervisorConnectionName | Specifies the HypervisorConnection objects to be removed by HypervisorConnectionName. | true | true (ByValue, ByPropertyName) |  |
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
c:\PS>Remove-HypHypervisorConnectionScope Finance -HypervisorConnectionUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
```
#### Description
Removes a single HypervisorConnection from the 'Finance' scope.
### Example 2
```
c:\PS>Remove-HypHypervisorConnectionScope Finance,Marketing -HypervisorConnectionUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
```
#### Description
Removes a single HypervisorConnection from multiple scopes.
### Example 3
```
c:\PS>Get-HypHypervisorConnection | Remove-HypHypervisorConnectionScope Finance
```
#### Description
Removes all visible HypervisorConnection objects from the 'Finance' scope.
### Example 4
```
c:\PS>Remove-HypHypervisorConnectionScope Finance -HypervisorConnectionName A\*
```
#### Description
Removes HypervisorConnection objects with a name starting with an 'A' from the 'Finance' scope.
