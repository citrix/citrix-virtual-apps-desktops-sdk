
# Disconnect-Brokersession
Disconnect a session.
## Syntax
```
Disconnect-BrokerSession [-InputObject] <Session[]> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Disconnects the specified session.

If the session is active, no warning is issued to the user before that session is disconnected.

After disconnection, sessions enter a Disconnected state. In a Disconnected state, a session still exists but there is no remote connection to that session.


## Related Commands

* [Get-BrokerSession](./Get-BrokerSession/)
* [Stop-BrokerSession](./Stop-BrokerSession/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Identifies the session(s) to disconnect. This can be expressed as either a session Uid or a session object. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Session
The sessions to disconnect can be piped into this cmdlet.
## Return Values

### None

## Notes
This operation is non-blocking and returns before it completes. The operation, however, is unlikely to fail unless there are communication problems between the controller and the machine, or if bad arguments are passed to the cmdlet itself or if the machine cannot successfully execute the operation.<br>    The transient nature of sessions means that the list of session objects or UIDs supplied to Disconnect-BrokerSession could consist of valid and invalid sessions. Invalid sessions are detected and disregarded and the disconnect session operation is invoked on only the valid sessions.<br>    The system can fail to disconnect the session if the machine is not in an appropriate state or if there are problems in communicating with the machine. When a disconnect is requested the system detects if the operation was initiated successfully or not by the machine. As this operation is non-blocking the system doesn't detect or report whether the disconnect ultimately succeeded or failed after it was started.<br>    Disconnect failures are reported through the broker SDK error handling mechanism (see about\_Broker\_ErrorHandling). In the event of errors the SdkErrorRecord error status is set to SessionOperationFailed and its error data dictionary is populated with the following entries:<br>    o OperationsAttemptedCount: The number of operations attempted.<br>    o OperationsFailedCount - The number of failed operations.<br>    o OperationsSucceededCount - The number of successfully executed operations.<br>    o UnresolvedSessionFailuresCount - The number of operations that failed due to invalid sessions being supplied.<br>    o OperationInvocationFailuresCount - The number of operations that failed because they could not be invoked on the machine.<br>    o DesktopExecutionFailuresCount - The number of operations that failed because they could not be successfully executed by the machine.<br>    The SdkErrorRecord message will also display the number of attempted, failed and successful operations in the following format:<br>    "Session operation error - attempted:&lt;OperationsAttemptedCount&gt;, failed:&lt;OperationsFailedCount&gt;, succeeded:&lt;OperationsSucceededCount&gt;"
## Examples

### Example 1
```
C:\PS> Get-BrokerSession -UserName MyDomain\MyAccount | Disconnect-BrokerSession
```
#### Description
Attempts to disconnect all of the sessions for the user MyDomain\\MyAccount.
### Example 2
```
C:\PS> $desktop = Get-BrokerDesktop -DNSName MyMachine.MyDomain.com

C:\PS> Disconnect-BrokerSession $desktop.SessionUid
```
#### Description
Disconnects the session on MyMachine.
### Example 3
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

C:\PS> Disconnect-BrokerSession -InputObject 10,11,12
```
#### Description
Attempts to disconnect sessions 10, 11 and 12. Traps and displays the error information.
