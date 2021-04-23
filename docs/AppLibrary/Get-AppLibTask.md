
# Get-Applibtask
Gets the task history for the AppLibrary Service.
## Syntax
```
Get-AppLibTask [[-TaskId] <Guid>] [-Type <JobType>] [-Active <Boolean>] [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns a list of tasks that have run or are currently running within the AppLibrary Service.


## Related Commands

* [Remove-AppLibTask](./Remove-AppLibTask/)
* [Stop-AppLibTask](./Stop-AppLibTask/)
* [Switch-AppLibTask](./Switch-AppLibTask/)
* [Add-AppLibTaskMetadata](./Add-AppLibTaskMetadata/)
* [Remove-AppLibTaskMetadata](./Remove-AppLibTaskMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the task identifier to be returned. | false | false |  |
| Type | Specifies the type of task to be returned. | false | false |  |
| Active | Specifies whether currently running tasks only or completed tasks only are returned. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
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

### 

## Notes
If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        One of the specified objects was not found.<br>    PartialData<br>         Only a subset of the available data was returned.<br>    InvalidFilter<br>        A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    CouldNotQueryDatabase<br>         The query required to get the database was not defined.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-AppLibTask -Active $false

TaskId                   : cfe5b3a2-c471-443e-b05e-8658e672d10f

Type                     : MyTask

Host                     : NYSERVER

Status                   : Finished

CurrentOperation         :

TaskProgress             : 100

TaskExpectedCompletion   : 10/10/2012 15:28:12

LastUpdateTime           : 10/10/2012 15:28:12

ActiveElapsedTime        : 56

DateFinished             : 10/10/2012 15:28:12

TerminatingError         :

...
```
#### Description
Get all completed tasks for the AppLibrary Service.&lt;br&gt;All tasks will publish at least the fields listed above, plus more related to the particular task being performed.
