
# Get-Brokersessionrecordingstatus
Gets the recording status of the specified session.
## Syntax
```
Get-BrokerSessionRecordingStatus [-Session] <Session> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Gets the recording status of the specified session.


## Related Commands

* [Start-BrokerSessionRecording](./Start-BrokerSessionRecording/)
* [Stop-BrokerSessionRecording](./Stop-BrokerSessionRecording/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Session | The session whose recording status to get. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Session
The session whose recording status to get.
## Return Values

### System.String
Get-BrokerSessionRecordingStatus returns a string representing whether or not the target session is being recorded.<br>Values can be:<br>o SessionBeingRecorded - Session is being recorded.<br>o SessionNotRecorded  - Session is not being recorded.
## Notes
The specified session can be passed using the Session parameter as a session object or a session Uid.
## Examples

### Example 1
```
C:\PS> Get-BrokerSessionRecordingStatus -Session 1
```
#### Description
Gets the recording status of the session Uid 1.
