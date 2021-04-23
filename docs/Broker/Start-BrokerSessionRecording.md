
# Start-Brokersessionrecording
Starts recording the specified session(s).
## Syntax
```
Start-BrokerSessionRecording [-Sessions] <Session[]> [-NotifyUser <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Start-BrokerSessionRecording [-User] <User> [-NotifyUser <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Starts recording the specified session(s).

Only active sessions using the HDX protocol can be recorded. An error appears when unqualified sessions (non-existent, inactive, or non-HDX) are specified for recording. No warning appears when you trigger an action to record sessions that are already being recorded.


## Related Commands

* [Get-BrokerSession](./Get-BrokerSession/)
* [Get-BrokerSessionRecordingStatus](./Get-BrokerSessionRecordingStatus/)
* [Stop-BrokerSessionRecording](./Stop-BrokerSessionRecording/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Sessions | Specifies the session(s) to be recorded. | true | true (ByValue) |  |
| User | Specifies the user whose session is to be recorded. | true | true (ByValue) |  |
| NotifyUser | Determines whether to notify the end user of the recording activity. | false | false | true |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Session
The session(s) to be recorded.
### Citrix.Broker.Admin.Sdk.User
The user whose sessions are to be recorded.
## Return Values

### None

## Notes
Sessions can be passed using the Sessions parameter as session objects or session Uids. A user can be passed using the User parameter as a user object or a user name.<br>    This operation is non-blocking and returns before it completes. The operation, however, is unlikely to fail unless there are communication problems between the Delivery Controller and the VDA, or if bad arguments are passed to the cmdlet itself, or if the VDA cannot successfully execute the operation.<br>    The Delivery Controller can fail to invoke the operation if the VDA is not in an appropriate state or if there are problems with communicating with the VDA. When an operation is invoked, the Delivery Controller detects and reports whether the operation is initiated successfully on the VDA. However, because the operation is non-blocking, the Delivery Controller does not detect or report whether or not the operation ultimately succeeds after the operation is initiated successfully.<br>    Operation failures are reported through the Broker SDK error handling mechanism (see about\_Broker\_ErrorHandling). In the event of errors, the SdkErrorRecord error status code is set to SessionOperationFailed and its error data dictionary is populated with the following entries:<br>    o OperationsAttemptedCount: The number of operations attempted.<br>    o OperationsFailedCount - The number of failed operations.<br>    o OperationsSucceededCount - The number of successful operations.<br>    The SdkErrorRecord message displays the number of attempted, failed, and successful operations in the following format:<br>    "Session operation error - attempted:&lt;OperationsAttemptedCount&gt;, failed:&lt;OperationsFailedCount&gt;, succeeded:&lt;OperationsSucceededCount&gt;"
## Examples

### Example 1
```
C:\PS> Start-BrokerSessionRecording -Sessions 10,11,12 -NotifyUser 0
```
#### Description
Starts recording the session Uid 10,11,12 without notifying the user.
### Example 2
```
C:\PS> Start-BrokerSessionRecording -User MYDOMAIN\Geffrey –NotifyUser 1
```
#### Description
Starts recording all sessions of user Geffrey in the domain named MYDOMAIN and notifies user Geffrey.
