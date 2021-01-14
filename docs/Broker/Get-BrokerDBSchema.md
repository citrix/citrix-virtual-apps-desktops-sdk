
# Get-Brokerdbschema
Gets SQL scripts to create or maintain the database schema for the Citrix Broker Service.
## Syntax
```
Get-BrokerDBSchema -DatabaseName <String> [-ServiceGroupName <String>] [-ScriptType <DatabaseScriptType>] [-SID <String>] [-LocalDatabase] [-DatabaseRights <String>] [-AzureDatabase] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Gets SQL scripts that can be used to create a new Citrix Broker Service database schema, add a new Broker service to an existing site, remove a Broker service from a site, or create a database server logon for a Broker service.

If no Sid parameter is provided, the scripts obtained relate to the currently selected Broker service instance, otherwise the scripts relate to Broker service instance running on the machine identified by the Sid provided. When obtaining the Evict script, a Sid parameter must be supplied.

The current service instance is the one on the local machine, or the one most recently specified using the -AdminAddress parameter of a Broker SDK cmdlet.

The service instance used to obtain the scripts does not need to be a member of a site or to have had its database connection configured.

The database scripts support only Microsoft SQL Server, or SQL Server Express, and require Windows integrated authentication to be used. They can be run using SQL Server's SQLCMD utility, or by copying the script into an SQL Server Management Studio (SSMS) query window and executing the query. If using SSMS, the query must be executed in 'SQLCMD mode'.

The ScriptType parameter determines which script is obtained. If ScriptType is not specified, or is FullDatabase, the script contains:


* Creation of service schema
* Creation of database server logon
* Creation of database user
* Addition of database user to Broker service roles

If ScriptType is Instance, the returned script contains:


* Creation of database server logon
* Creation of database user
* Addition of database user to Broker service roles

If ScriptType is Evict, the returned script contains:


* Removal of Broker service instance from database
* Removal of database user

If ScriptType is Login, the returned script contains:


* Creation of database server logon only

ScriptType Database is deprecated, and FullDatabase should be used instead.

If the service uses two data stores they can exist in the same database.

You do not need to configure a database before using this command.


## Related Commands

* [Set-BrokerDBConnection](./Set-BrokerDBConnection/)
* [Test-BrokerDBConnection](./Test-BrokerDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DatabaseName | Specifies the name of the database into which the new Broker service schema is to be placed, or in which it already exists. The database itself is not created by any of the script types; it must already exist before the scripts are run. | true | false |  |
| ServiceGroupName | Specifies the name of the service group to be used when creating the database schema. The service group is a collection of all the Broker services that share the same database instance and are considered equivalent; that is, all the services within a service group can be used interchangeably. | false | false |  |
| ScriptType | Specifies the type of database script returned. Available script types are:<br>-- FullDatabase<br>Creates a database schema for the Citrix Broker Service in a database instance that does not already contain one. This is used when creating a new site. DatabaseName and ServiceGroupName are required parameters for this script type.<br>-- Instance<br>Adds a Broker Service instance to a database and so to the associated site. Appropriate database server logons and users are created to allow the service instance access to the required service schemas.<br>-- Evict<br>Removes a Broker Service instance from the database and so from the site. All reference to the service instance is removed from the database. DatabaseName and Sid are required parameters for this script type.<br>-- Login<br>Adds a logon for the Broker Service instance to a database server. This is specifically for use when configuring SQL Server mirroring where the mirror server must have appropriate logons created for all service instances in the site.<br>-- Database<br>This is deprecated. FullDatabase should be used instead. | false | false |  |
| SID | Specifies the SID of the controller on which the Broker Service instance to remove from the database is running (only valid for a script type of Evict). | false | false | None |
| LocalDatabase | Specifies whether the database script is to be used in a database instance run on the same controller as other services in the service group. Including this parameter ensures the script creates only the required permissions for local services to access the database schema for Broker services. If this parameter is specified inappropriately, the service instance will not be able to connect to the database. | false | false |  |
| DatabaseRights | Specifies the right the database script should expect to be run under.  Available rights are:<br>-- Mixed<br>Creates a database schema which uses all rights.<br>-- SysAdmin<br>Creates a database schema which does the minimum with the SysAdmin (sa) rights.<br>-- DbOwner<br>Creates a database schema which only needs Database Owner (dbo) rights. This script expects to be used after the SysAdmin script has been run. | false | false | Mixed |
| AzureDatabase | Specifies that the generated schema must be compatible with Azure SQL limits, including not generating code for logins. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
A string containing the required SQL script for applying to a database.
## Notes
The scripts returned support Microsoft SQL Server Express Edition, Microsoft SQL Server Standard Edition, and Microsoft SQL Server Enterprise Edition databases only, and are generated on the assumption that integrated authentication will be used.<br>    If the ScriptType parameter is not included or set to 'FullDatabase', the full database script is returned, which will:<br>        Create the database schema.<br>        Create the user and the role (providing the schema does not already exist).<br>        Create the logon (providing the schema does not already exist).<br>    If the ScriptType parameter is set to 'Instance', the script will:<br>        Create the user and the role (providing the schema does not already exist).<br>        Create the logon (providing the schema does not already exist) and associate it with a user.<br>    If the ScriptType parameter is set to 'Login', the script will:<br>        Create the logon (providing the schema does not already exist) and associate it with a pre-existing user of the same name.<br>    ScriptType value of 'Database' is deprecated; 'FullDatabase' should be used instead.<br>    If the LocalDatabase parameter is included, the NetworkService account will be added to the list of accounts permitted to access the database. This is required only if the database is run on a controller.<br>    If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    GetSchemasFailed<br>        The database schema could not be found.<br>    ActiveDirectoryAccountResolutionFailed<br>        The specified Active Directory account or Group could not be found.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-BrokerDBSchema -DatabaseName MySiteDB -ServiceGroupName  MyServiceGroup > C:\BrokerSchema.sql
```
#### Description
Gets a script to create the full database schema for the Citrix Broker Service and copies it to a file called "C:\\BrokerSchema.sql"&lt;br&gt;This script can be used to create the service schema in a database with name "MySiteDB", which must already exist, and must not already contain a Broker service schema.
### Example 2
```
C:\PS>Get-BrokerDBSchema -DatabaseName MySiteDB -ScriptType Login > C:\BrokerLogins.sql
```
#### Description
Gets a script to create the appropriate database server logon for the Broker service. This can be used when configuring a mirror server for use.
