
# Remove-Applibappdiskscope
Remove the specified AppDisk(s) from the given scope(s).
## Syntax
```
Remove-AppLibAppDiskScope [-Scope] <String[]> -InputObject <AppDisk[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibAppDiskScope [-Scope] <String[]> -AppDiskUid <Guid[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Remove-AppLibAppDiskScope [-Scope] <String[]> -AppDiskName <String[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-AppLibAppDiskScope command is used to remove one or more AppDisk objects from the given scope(s).

There are multiple parameter sets for this cmdlet, allowing you to identify the AppDisk objects in different ways: - AppDisk objects can be piped in or specified by the InputObject parameter - The AppDiskUid parameter specifies objects by AppDiskUid - The AppDiskName parameter specifies objects by AppDiskName (supports wildcards)

To remove a AppDisk from a scope you need permission to change the scopes of the AppDisk.

If the AppDisk is not in a specified scope, that scope will be silently ignored.


## Related Commands

* [Add-AppLibAppDiskScope](./Add-AppLibAppDiskScope/)
* [Get-AppLibScopedObject](./Get-AppLibScopedObject/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Scope | Specifies the scopes to remove the objects from. | true | false |  |
| InputObject | Specifies the AppDisk objects to be removed. | true | true (ByValue, ByPropertyName) |  |
| AppDiskUid | Specifies the AppDisk objects to be removed by AppDiskUid. | true | true (ByValue, ByPropertyName) |  |
| AppDiskName | Specifies the AppDisk objects to be removed by AppDiskName. | true | true (ByValue, ByPropertyName) |  |
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
c:\PS>Remove-AppLibAppDiskScope Finance -AppDiskUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
```
#### Description
Removes a single AppDisk from the 'Finance' scope.
### Example 2
```
c:\PS>Remove-AppLibAppDiskScope Finance,Marketing -AppDiskUid 6702C5D0-C073-4080-A0EE-EC74CB537C52
```
#### Description
Removes a single AppDisk from multiple scopes.
### Example 3
```
c:\PS>Get-AppLibAppDisk | Remove-AppLibAppDiskScope Finance
```
#### Description
Removes all visible AppDisk objects from the 'Finance' scope.
### Example 4
```
c:\PS>Remove-AppLibAppDiskScope Finance -AppDiskName A\*
```
#### Description
Removes AppDisk objects with a name starting with an 'A' from the 'Finance' scope.
