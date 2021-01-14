
# Get-Applibappdiskstartmenuicon
Gets the AppDisk start menu icons for the AppLibrary Service.
## Syntax
```
Get-AppLibAppDiskStartMenuIcon [-AppDiskUid <Guid>] [-AppDiskName <String>] [-IconUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns a list of AppDisk start menu icons known to the AppLibrary Service.


## Related Commands

* [Get-AppLibAppDisk](./Get-AppLibAppDisk/)
* [Get-AppLibAppDiskStartMenuShortcut](./Get-AppLibAppDiskStartMenuShortcut/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskUid | The identifier of a specific AppDisk to inspect. | false | false |  |
| AppDiskName | The name of a specific AppDisk to inspect. | false | false |  |
| IconUid | The identifier of a specific icon to inspect. | false | false |  |
| ReturnTotalRecordCount | See about\_AppLib\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_AppLib\_Filtering for details. | false | false | false |
| Skip | See about\_AppLib\_Filtering for details. | false | false | 0 |
| SortBy | See about\_AppLib\_Filtering for details. | false | false |  |
| Filter | See about\_AppLib\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appdiskshortcuticon
This object provides details of the icon and its use, and contains the following information: IconUid &lt;Guid&gt; The identifier for the icon IconData &lt;string&gt; The icon data, Base-64 encoded as a string AppDiskUid &lt;Guid&gt; The identifier for the owning AppDisk
## Notes
If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        One of the specified objects was not found.<br>    PartialData<br>         Only a subset of the available data was returned.<br>    InvalidFilter<br>        A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    CouldNotQueryDatabase<br>         The query required to get the database was not defined.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-AppLibStartMenuIcon -AppDiskName MyAppDisk

          AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e

          IconUid                  : 7b4c01c4-72fa-4c80-913d-c6df785f4297

          IconData                 : "7Z3rc+I2EMC/d6b/A8PXBj94JTDAzJVLepnm1UDvMr25uQpbcCq2RCU5Cenc/1...."

          AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e

          IconUid                  : 4c245ff7-5cdd-4aac-a854-1e101e23d1f6

          IconData                 : "s/HMKy5JzEtOVYAxPFNslVINE9NMDNPMdU0Sk5J0TYyT0nQtLFPTdFPNTRJTjQ...."

          ...
```
#### Description
Get all start menu icons for the AppLDisk "MyAppDisk".
### Example 2
```
c:\PS>Get-AppLibStartMenuIcon -IconUid "7b4c01c4-72fa-4c80-913d-c6df785f4297"

          AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e

          IconUid                  : 7b4c01c4-72fa-4c80-913d-c6df785f4297

          IconData                 : "7Z3rc+I2EMC/d6b/A8PXBj94JTDAzJVLepnm1UDvMr25uQpbcCq2RCU5Cenc/1...."
```
#### Description
Get the specific start menu icon "7b4c01c4-72fa-4c80-913d-c6df785f4297".
