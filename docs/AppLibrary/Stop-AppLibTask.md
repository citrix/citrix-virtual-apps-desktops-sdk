
# Stop-Applibtask
Stops currently running AppLibrary Service tasks.
## Syntax
```
Stop-AppLibTask [-TaskId] <Guid> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Enables tasks currently running in the AppLibrary Service to be stopped.  Once stopped, tasks cannot be restarted.


## Related Commands

* [Get-AppLibTask](./Get-AppLibTask/)
* [Remove-AppLibTask](./Remove-AppLibTask/)
* [Switch-AppLibTask](./Switch-AppLibTask/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TaskId | Specifies the identifier for the task to be stopped. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.Management.Automation.Psobject
Objects containing the TaskId parameter can be piped to the Stop-AppLibTask command.
## Return Values

### 

## Notes
If the command fails, the following errors can result.<br>    Error Codes<br>    -----------<br>    InvalidWorkflow<br>        The specified task could not be found.<br>    InvalidWorkflowHost<br>        The specified task is executing on a different server.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    DatabaseError<br>        There was a problem communicating with the database.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-AppLibTask -active $true | Stop-AppLibTask

Success
```
#### Description
Terminate all tasks currently executing on the AppLibrary Service.
### Example 2
```
c:\PS>Stop-AppLibTask -TaskId bd52e688-e40d-4790-83de-9f7633481454

Success
```
#### Description
Terminate the named task executing on the AppLibrary Service.
