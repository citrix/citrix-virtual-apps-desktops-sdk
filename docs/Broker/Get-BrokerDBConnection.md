
# Get-Brokerdbconnection
Gets the database connection string for the specified data store used by the Broker Service.
## Syntax
```
Get-BrokerDBConnection [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Gets the database connection string from the currently selected Broker Service instance.

If the returned string is blank, no valid connection string has been specified. In this case the service is running, but is idle and awaiting specification of a valid connection string.

The current service instance is the one on the local machine, or the one most recently specified using the -AdminAddress parameter of a Broker SDK cmdlet.


## Related Commands

* [Set-BrokerDBConnection](./Set-BrokerDBConnection/)
* [Get-BrokerServiceStatus](./Get-BrokerServiceStatus/)
* [Test-BrokerDBConnection](./Test-BrokerDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
The database connection string configured for the current Broker Service instance.
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    NoDBConnections<br>        The database connection string for the Broker Service has not been specified.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
C:\PS> Get-BrokerDBConnection -AdminAddress controller1.mydomain.net
```
#### Description
Gets the database connection string in use by the Broker Service instance running on controller "controller1.mydomain.net".
