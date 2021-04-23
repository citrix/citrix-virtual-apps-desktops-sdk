
# Get-Logservicestatus
Gets the current status of the ConfigurationLogging Service on the controller.
## Syntax
```
Get-LogServiceStatus [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Enables the status of the ConfigurationLogging Service on the controller to be determined. If the service has multiple data stores it will return the overall state as an aggregate of all the data store states. For example, if the site data store status is OK and the secondary data store status is DBUnconfigured then it will return DBUnconfigured. The database connection to the service does not need to be configured before using this command.


## Related Commands

* [Get-LogDataStore](./Get-LogDataStore/)
* [Set-LogDBConnection](./Set-LogDBConnection/)
* [Test-LogDBConnection](./Test-LogDBConnection/)
* [Get-LogDBConnection](./Get-LogDBConnection/)
* [Get-LogDBSchema](./Get-LogDBSchema/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Fma.Sdk.Utilities.Service.Servicestatusinfo
The Get-LogServiceStatus command returns an object containing the status of the ConfigurationLogging Service together with extra diagnostics information.<br>OK<br>    The ConfigurationLogging Service is running and is connected to a database containing a valid schema.<br>DBUnconfigured<br>    The ConfigurationLogging Service does not have a database connection configured.<br>DBRejectedConnection<br>    The database rejected the logon attempt from the ConfigurationLogging Service.  This may be because the service attempted to log on with invalid credentials or because a database has not been installed in the specified location.<br>InvalidDBConfigured<br>    The expected stored procedures are missing from the database.  This may be because the ConfigurationLogging Service schema has not been added to the database.<br>DBNotFound<br>    The specified database could not be located with the configured connection string.<br>DBMissingOptionalFeature<br>    The ConfigurationLogging is connected to a database that is valid, but it does not have the full functionality required for optimal performance. Upgrading the database is advisable.<br>DBMissingMandatoryFeature<br>    The ConfigurationLogging is connected to a database that is valid, but it does not have the full functionality required so the ConfigurationLogging cannot function. Upgrading the database is required.<br>DBNewerVersionThanService<br>    The version of the ConfigurationLogging Service currently in use is incompatible with the version of the ConfigurationLogging Service schema on the database.  Upgrade the ConfigurationLogging Service to a more recent version.<br>DBOlderVersionThanService<br>    The version of the ConfigurationLogging Service schema on the database is incompatible with the version of the ConfigurationLogging Service currently in use.  Upgrade the database schema to a more recent version.<br>DBVersionChangeInProgress<br>    A database schema upgrade is currently in progress.<br>PendingFailure<br>    Connectivity between the ConfigurationLogging Service and the database has been lost. This may be a transitory network error, but may indicate a loss of connectivity that requires administrator intervention.<br>Failed<br>    Connectivity between the ConfigurationLogging and the database has been lost for an extended period of time, or has failed due to a configuration problem. The ConfigurationLogging service cannot operate while its connection to the database is unavailable.<br>Unknown<br>    (0) The service status cannot be determined.
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-LogServiceStatus

DBUnconfigured
```
#### Description
Get the current status of the ConfigurationLogging Service.
