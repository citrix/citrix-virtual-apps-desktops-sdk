
# Set-Acctdbconnection
Configures a database connection for the ADIdentity Service.
## Syntax
```
Set-AcctDBConnection [-DBConnection] <String> [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Specifies the database connection string for use by the currently selected Citrix ADIdentity Service instance.

The service records the connection string and attempts to contact the specified database. If the database cannot initially be contacted the service retries the connection at intervals until contact with the database is successfully established.

Is is not possible to set a new database connection string for the service if one is already recorded. The connection string must first be set to \$null. This action causes the service to reset and return to its idle state, at which point a new connection string can be set.

When a database connection string is successfully set for the service, a status of OK is returned by the cmdlet. If the database connection string is set to \$null, a DBUnconfigured status is returned.

A syntactically invalid connection string is not recorded.

Only use of Windows authentication within the connection string is supported; a connection string containing SQL authentication credentials is always rejected as invalid.

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a ADIdentity SDK cmdlet.


## Related Commands

* [Get-AcctServiceStatus](./Get-AcctServiceStatus/)
* [Get-AcctDBConnection](./Get-AcctDBConnection/)
* [Test-AcctDBConnection](./Test-AcctDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DBConnection | Specifies the database connection string to be used by the ADIdentity Service.  Passing in \$null will clear any existing database connection configured. | true | false |  |
| Force | If present, allows the local administrator to set the connection string to null when there are problems contacting the database or other services. | false | false | false |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Fma.Sdk.Utilities.Service.Servicestatusinfo
The Set-AcctDBConnection cmdlet returns an object describing the status of the ADIdentity Service together with extra diagnostics information. Possible values are:<br>-- OK:<br>The ADIdentity Service instance is configured with a valid database and service schema. The service is operational.<br>-- DBUnconfigured:<br>No database connection string is set for the ADIdentity Service instance.<br>-- DBRejectedConnection:<br>The database rejected the logon attempt from the ADIdentity Service. This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.<br>-- InvalidDBConfigured:<br>The specified database does not exist, is not visible to the ADIdentity Service instance, or the service's schema within the database is invalid.<br>-- DBNotFound:<br>The specified database could not be located with the configured connection string.<br>-- DBNewerVersionThanService:<br>The version of the ADIdentity Service currently in use is newer than, and incompatible with, the version of the ADIdentity Service schema on the database. Upgrade the ADIdentity Service to a more recent version.<br>-- DBOlderVersionThanService:<br>The version of the ADIdentity Service schema on the database is newer than, and incompatible with, the version of the ADIdentity Service currently in use. Upgrade the database schema to a more recent version.<br>-- DBVersionChangeInProgress:<br>A database schema upgrade is in progress.<br>-- PendingFailure:<br>Connectivity between the ADIdentity Service instance and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.<br>-- Failed:<br>Connectivity between the ADIdentity Service instance and the database has been lost for an extended period of time, or has failed due to a configuration problem. The service instance cannot operate while its connection to the database is unavailable.<br>-- Unknown:<br>The status of the ADIdentity Service cannot be determined.
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    InvalidDBConnectionString<br>        The database connection string has an invalid format.<br>    DatabaseConnectionDetailsAlreadyConfigured<br>        There was already a database connection configured. After a configuration is set, it can only be set to \$null.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Set-AcctDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
```
#### Description
Configures the service instance to use a database called XDDB on an SQL Server Express database running on the machine called dbserver. Integrated Windows authentication is required.
### Example 2
```
C:\PS>Set-AcctDBConnection -DBConnection $null
```
#### Description
Resets the service instance's database connection string. The service instance resets and returns to an idle state until a valid new database connection string is specified.
### Example 3
```
c:\PS>Set-AcctDBConnection -DBConnection "Server=serverName\SQLEXPRESS;Initial Catalog = databaseName;  Integrated Security = True"

          OK
```
#### Description
Configures a database connection string for the ADIdentity Service.
### Example 4
```
c:\PS>Set-AcctDBConnection -DBConnection "Invalid Connection String"

          Invalid database connection string format.
```
#### Description
Configures an invalid database connection string for the ADIdentity Service.
