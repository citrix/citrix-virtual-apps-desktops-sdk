
# Test-Envtestdbconnection
Tests whether a database is suitable for use by the Citrix EnvTest Service.
## Syntax
```
Test-EnvTestDBConnection [-DBConnection] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Tests whether the database specified in the given connection string is suitable for use by the currently selected Citrix EnvTest Service instance.

The service attempts to contact the specified database and returns a status indicating whether the database is both contactable and usable. The test does not impact any currently established connection from the service instance to another database in any way. The tested connection string is not recorded.

Only use of Windows authentication within the connection string is supported; a connection string containing SQL authentication credentials is always rejected as invalid.

The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a EnvTest SDK cmdlet.


## Related Commands

* [Get-EnvTestServiceStatus](./Get-EnvTestServiceStatus/)
* [Get-EnvTestDBConnection](./Get-EnvTestDBConnection/)
* [Set-EnvTestDBConnection](./Set-EnvTestDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DBConnection | Specifies the database connection string to be tested by the currently selected Citrix EnvTest Service instance. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Fma.Sdk.Utilities.Service.Servicestatusinfo
The Test-EnvTestDBConnection cmdlet returns an object of type ServiceStatusInfo describing the changes to the system that would result from using the specified connection string with the Set-EnvTestDBConnection cmdlet. The actual state of the system is not changed.<br>The returned ServiceStatusInfo object has two properties: ServiceStatus, which gives the status of the selected EnvTest Service instance that would result from adopting the connection string, and ExtraInfo, which is a dictionary providing extra diagnostics information for the database identified by the connection string.<br>Possible ServiceStatus values are:<br>-- OK:<br>The Set-EnvTestDBConnection command would succeed if it were executed with the supplied connection string.<br>-- DBUnconfigured:<br>No database connection string is set for the service instance.<br>-- DBRejectedConnection:<br>The database rejected the logon attempt from the EnvTest Service instance. This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.<br>-- InvalidDBConfigured:<br>The specified database does not exist, is not visible to the EnvTest Service instance, or the service's schema within the database is invalid.<br>-- DBNotFound:<br>The specified database could not be located with the given connection string.<br>-- DBNewerVersionThanService:<br>The EnvTest Service instance is older than, and incompatible with, the service's schema in the database. The service instance needs upgrading.<br>-- DBOlderVersionThanService:<br>The EnvTest Service instance is newer than, and incompatible with, the service's schema in the database. The database schema needs upgrading.<br>-- DBVersionChangeInProgress:<br>A database schema upgrade is currently in progress.<br>-- PendingFailure:<br>Connectivity between the EnvTest Service instance and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.<br>-- Failed:<br>Connectivity between the EnvTest Service instance and the database has been lost for an extended period of time, or has failed due to a configuration problem. The service instance cannot operate while its connection to the database is unavailable.<br>-- Unknown:<br>Service status cannot be determined.<br>The ExtraInfo dictionary contains at least the following keys, and their associated string values:<br>-- Server.Version:<br>Database server version number.<br>-- Server.IsClustered:<br>"True" if the database server is clustered; "False" otherwise.<br>-- Database.Status:<br>Status of the database. When operating normally, the value is "Normal".<br>-- Database.RecoveryModel:<br>Recovery model of the database (e.g. "Simple").<br>-- Database.LastBackupDate:<br>Date of the last backup of this database.<br>-- Database.IsReadCommittedSnapshotOn:<br>"True" if the READ\_COMMITTED\_SNAPSHOT database option is enabled; "False" otherwise.<br>-- Database.Collation:<br>Collation order of the database (e.g. "Latin1\_General\_100\_CI\_AS\_KS").<br>-- Database.IsMirroringEnabled:<br>"True" if the database is mirrored; "False" otherwise.<br>-- Database.AvailabilityGroupName:<br>The name of the availability group of which this database is a member.<br>Beware that the corresponding values are always strings. Therefore, to test Boolean values, you must use statements like<br>if (\$info\["Server.IsClustered"\] == "True")<br>instead of just<br>if (\$info\["Server.IsClustered"\])
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    InvalidDBConnectionString<br>        The database connection string has an invalid format.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Test-EnvTestDBConnection "Server=dbserver\SQLEXPRESS;Database=XDDB;Trusted_Connection=True"
```
#### Description
Tests whether the service instance could use a database called XDDB on an SQL Server Express database running on the machine called dbserver. Integrated Windows authentication is required.
### Example 2
```
c:\PS>Test-EnvTestDBConnection -DBConnection "Invalid Connection String"

          Invalid database connection string format.
```
#### Description
Tests an invalid database connection string for the EnvTest Service.
