
# Remove-Applibappvpackage
Removes an App-V package from the library that is holding it
## Syntax
```
Remove-AppLibAppVPackage [-Uid] <Int32> [-ServerUid <Int32>] [-Purge <Boolean>] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to remove an App-V package from the application library.

Removing a package from the library optionally only marks it as not existing. In this case, re-adding the package later will restore the reference.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | The App Library's internal unique identifier of the App-V package. | true | true (ByValue, ByPropertyName) |  |
| ServerUid | Unique Identifier for AppVServer. | false | true (ByValue, ByPropertyName) |  |
| Purge | Indicates whether the package should be removed from the database. The default is true. Setting this parameter to false will leave the package and all of its associated applications and metadata in place but in a dormant state. This data will then be reactivated if the same package is ever re-added. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### None

## Notes
If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        No package was found for the given uid. DatabaseError<br>        An error occurred in the service while attempting a database operation. DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured. DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. PermissionDenied<br>        You do not have permission to execute this command. AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service. CommunicationError<br>        There was a problem communicating with the remote service. ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
Remove-AppLibAppVPackage -Uid 5
```
#### Description
Permanently removes the specified package from the library including its associated applications and metadata.
### Example 2
```
Remove-AppLibAppVPackage -Uid 5 -Purge $true
```
#### Description
Permanently removes the specified package from the library including its associated applications and metadata.
### Example 3
```
Remove-AppLibAppVPackage -Uid 5 -Purge $false
```
#### Description
Removes the specified package from the library that holds it by marking it as non-existing, but leaving associated records and metadata in place.
