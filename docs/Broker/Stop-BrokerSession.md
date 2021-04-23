
# Stop-Brokersession
Stop or log off a session.
## Syntax
```
Stop-BrokerSession [-InputObject] <Session[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Stops or logs off sessions.


## Related Commands

* [Disconnect-BrokerSession](./Disconnect-BrokerSession/)
* [Get-BrokerSession](./Get-BrokerSession/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Identifies the session(s) to terminate. This can be expressed as either a session Uid or a session object. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Session
The sessions to stop can be piped into this cmdlet.
## Return Values

### None

## Notes
This operation is non-blocking and returns before it completes. The operation, however, is unlikely to fail unless there are communication problems between the controller and the machine, if bad arguments are passed to the cmdlet itself or if the machine cannot successfully execute the operation.<br>    The transient nature of sessions means that the list of session objects or UIDs supplied to Stop-BrokerSession could consist of valid and invalid sessions. Invalid sessions are detected and disregarded and the stop session operation is invoked on the valid sessions.<br>    The system can fail to invoke the operation if the machine is not in an appropriate state or if there are problems in communicating with the machine. When an operation is invoked the system detects if the operation was initiated successfully or not by the machine. As this operation is non-blocking the system doesn't detect or report whether the operation ultimately succeeded or failed after its successful initialization on the machine.<br>    Operation failures are reported through the broker SDK error handling mechanism (see about\_Broker\_ErrorHandling). In the event of errors the SdkErrorRecord error status is set to SessionOperationFailed and its error data dictionary is populated with the following entries:<br>    o OperationsAttemptedCount - The number of operations attempted.<br>    o OperationsFailedCount - The number of failed operations.<br>    o OperationsSucceededCount - The number of successfully executed operations.<br>    o UnresolvedSessionFailuresCount - The number of operations that failed due to invalid sessions being supplied.<br>    o OperationInvocationFailuresCount - The number of operations that failed because they could not be invoked on the desktop.<br>    o DesktopExecutionFailuresCount - The number of operations that failed because they could not be successfully executed by the desktop.<br>    The SdkErrorRecord message will also display the number of attempted, failed and successful operations in the following format:<br>    "Session operation error - attempted:&lt;OperationsAttemptedCount&gt;, failed:&lt;OperationsFailedCount&gt;, succeeded:&lt;OperationsSucceededCount&gt;"
## Examples

### Example 1
```
C:\PS> Get-BrokerSession -UserName MyDomain\MyAccount | Stop-BrokerSession
```
#### Description
Stops all sessions for the user MyDomain\\MyAccount.
### Example 2
```
C:\PS> $desktop = Get-BrokerDesktop -DNSName MyMachine.MyDomain.com

C:\PS> Stop-BrokerSession $desktop.SessionUid
```
#### Description
Stops the session on MyMachine.
### Example 3
```
C:\PS> Get-BrokerSession -Filter { SessionState -eq 'Disconnected' -and SessionStateChangeTime -lt '-1' } | Stop-BrokerSession
```
#### Description
Stop sessions that have been disconnected for more than one day.
### Example 4
```
C:\PS> trap  [Citrix.Broker.Admin.SDK.SdkOperationException]

C:\PS> {

C:\PS>   write $("Exception name = " + $_.Exception.GetType().FullName)

C:\PS>   write $("SdkOperationException.Status = " + $_.Exception.Status)

C:\PS>   write $("SdkOperationException.ErrorData=")

C:\PS>   $_.Exception.ErrorData

C:\PS>

C:\PS>   write $("SdkOperationException.InnerException = " + $_.Exception.InnerException)

C:\PS>   $_.Exception.InnerException

C:\PS>   continue

C:\PS> }

C:\PS>

C:\PS> Stop-BrokerSession -InputObject 10,11,12
```
#### Description
Trap and display error information.
