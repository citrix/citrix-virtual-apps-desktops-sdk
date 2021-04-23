
# Get-Hypinstalleddbversion
Gets a list of all available database schema versions for the Host Service.
## Syntax
```
Get-HypInstalledDBVersion [-Upgrade] [-Downgrade] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Gets the current version number of the Citrix Host Service database schema when called with no parameters.

When called with the -Upgrade parameter, gets the service schema version numbers to which an upgrade could be performed.

When called with the -Downgrade parameter, gets the service schema version numbers to which a downgrade could be performed.

The SQL scripts to perform schema upgrades and downgrades can be obtained using the Get-HypDBVersionChangeScript cmdlet. Citrix recommends that where possible service schema upgrades are performed using Studio rather than manually via the SDK.

Only one of the -Upgrade or -Downgrade parameters may be supplied at once.


## Related Commands

* [Get-HypDBVersionChangeScript](./Get-HypDBVersionChangeScript/)
* [Get-HypDBSchema](./Get-HypDBSchema/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Upgrade | Specifies that only schema versions to which the current database version can be updated should be returned. | false | false |  |
| Downgrade | Specifies that only schema versions to which the current database version can be reverted should be returned. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.Version
Get-HypInstalledDBVersion returns database schema version numbers as requested.<br>Major &lt;Integer&gt; Minor &lt;Integer&gt; Build &lt;Integer&gt; Revision &lt;Integer&gt;
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    InvalidParameterCombination<br>        Both the Upgrade and Downgrade flags were specified.<br>    NoOp<br>        The operation was successful but had no effect.<br>    NoDBConnections<br>        The database connection string for the Host Service has not been specified.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
PS C:\>Get-HypInstalledDBVersion

Major  Minor  Build  Revision

-----  -----  -----  --------

5      6      0      0
```
#### Description
Gets the current Citrix Host Service database schema version number.
### Example 2
```
C:\PS>Get-HypInstalledDBVersion -Upgrade
```
#### Description
Get the versions of the Host Service database schema for which upgrade scripts are supplied.
