
# Get-Applibappdiskstartmenushortcut
Gets the AppDisk start menu shortcuts for the AppLibrary Service.
## Syntax
```
Get-AppLibAppDiskStartMenuShortcut [-StartMenuShortcutUid <Guid>] [-AppDiskUid <Guid>] [-AppDiskName <String>] [-CommandLineExecutable <String>] [-CommandLineArguments <String>] [-Description <String>] [-DisplayName <String>] [-ShortcutPath <String>] [-WorkingDirectory <String>] [-IconUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns a list of AppDisk shortcuts known to the AppLibrary Service.


## Related Commands

* [Get-AppLibAppDisk](./Get-AppLibAppDisk/)
* [Get-AppLibAppDiskStartMenuIcon](./Get-AppLibAppDiskStartMenuIcon/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| StartMenuShortcutUid | The identifier of a specific shortcut to inspect. | false | false |  |
| AppDiskUid | The identifier of a specific AppDisk to inspect. | false | false |  |
| AppDiskName | The name of a specific AppDisk to inspect. | false | false |  |
| CommandLineExecutable | The executable indicated by the shortcut to match | false | false |  |
| CommandLineArguments | The command line argument string of a shortcut to match | false | false |  |
| Description | The description of the shortcut to match | false | false |  |
| DisplayName | The displayed name of the shortcut to match | false | false |  |
| ShortcutPath | The path of the shortcut to match | false | false |  |
| WorkingDirectory | The working directory of the shortcut to match | false | false |  |
| IconUid | The identifier of a specific icon to inspect. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_AppLib\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_AppLib\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appdiskshortcut
This object provides details of the shortcut and its use, and contains the following information: AppDiskUid &lt;Guid&gt; The identifier for the owning AppDisk AppDiskName &lt;string&gt; The identifier for the owning AppDisk IconUid &lt;Guid&gt; The identifier for the icon, if present CommandLineExecutable &lt;string&gt; The shortcut executable property CommandLineArguments &lt;string&gt; The shortcut arguments property Description &lt;string&gt; The shortcut description property DisplayName &lt;string&gt; The shortcut display name property ShortcutPath &lt;string&gt; The shortcut path property WorkingDirectory &lt;string&gt; The shortcut working directory property
## Notes
If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        One of the specified objects was not found.<br>    PartialData<br>         Only a subset of the available data was returned.<br>    InvalidFilter<br>        A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    CouldNotQueryDatabase<br>         The query required to get the database was not defined.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-AppLibStartMenuIcon -AppDiskName MyAppDisk

          AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e

          AppDiskName              : MyAppDisk

          IconUid                  : 7b4c01c4-72fa-4c80-913d-c6df785f4297

          CommandLineExecutable    : "C:\Program Files (x86)\Mozilla Firefox\firefox.exe"

          CommandLineArguments     :

          Description              :

          DisplayName              : Mozilla Firefox

          ShortcutPath             : "C:\Users\Public\Desktop\Mozilla Firefox.lnk"

          WorkingDirectory         : "C:\Program Files (x86)\Mozilla Firefox"

          AppDiskUid               : d9ba6487-05f8-48ad-a178-1794605e2b8e

          AppDiskName              : MyAppDisk

          ...
```
#### Description
Get all shortcuts for the AppLDisk "MyAppDisk".
