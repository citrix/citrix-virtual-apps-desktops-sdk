
# Get-Applibappdiskobjectreference
Returns the number of objects holding references to AppDisks.
## Syntax
```
Get-AppLibAppDiskObjectReference -AppDiskUid <Guid> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Get-AppLibAppDiskObjectReference [-AppDiskName] <String> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns, for a given AppDisk name or UID, the number of references by objects in other services (e.g. Broker Desktop Groups).


## Related Commands

* [Get-AppLibAppDisk](./Get-AppLibAppDisk/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk. | true | false |  |
| AppDiskUid | The unique identifier of the AppDisk. | true | true (ByPropertyName) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appdiskreferences
This object provides details of the AppDisk and contains the following information:<br>          AppDiskUid &lt;Guid&gt;<br>          The unique identifier for the AppDisk.<br>          AppDiskName &lt;string&gt;<br>          The name of the AppDisk.<br>          References &lt;AppDiskUsage\[\]&gt;<br>          Objects specifying the referencing type (e.g. Broker Desktop Group) and the number of references by objects of that type.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-AppLibAppDiskObjectReference -AppDiskUid 7585f0de-192e-4847-a6d8-22713c3a2f42

          AppDiskUid    : 7585f0de-192e-4847-a6d8-22713c3a2f42

          AppDiskName   : Disk1

          References    : {Citrix.AppLibrary.Sdk.AppDiskUsage}
```
#### Description
Returns the references to an AppDisk referenced by UID.
### Example 2
```
C:\PS>Get-AppLibAppDiskObjectReference -AppDiskUid Disk1

          AppDiskUid    : 7585f0de-192e-4847-a6d8-22713c3a2f42

          AppDiskName   : Disk1

          References    : {Citrix.AppLibrary.Sdk.AppDiskUsage}
```
#### Description
Returns the references to an AppDisk referenced by name.
