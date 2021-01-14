
# Get-Trustdbconnection
Gets the database string for the specified data store used by the Trust Service.
## Syntax
```
Get-TrustDBConnection [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns the database connection string from the currently selected Trust Service instance.

If the returned string is blank, no valid connection string has been specified. In this case the service is running, but is idle and awaiting specification of a valid connection string.

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a Trust SDK cmdlet.


## Related Commands

* [Get-TrustServiceStatus](./Get-TrustServiceStatus/)
* [Set-TrustDBConnection](./Set-TrustDBConnection/)
* [Test-TrustDBConnection](./Test-TrustDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
The database connection string configured for the current Trust Service instance.
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    NoDBConnections<br>        The database connection string for the Trust Service has not been specified.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-TrustDBConnection

Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True
```
#### Description
Get the database connection string for the Trust Service.
