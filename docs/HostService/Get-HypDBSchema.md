
# Get-Hypdbschema
Gets SQL scripts to create or maintain the database schema for the Citrix Host Service.
## Syntax
```
Get-HypDBSchema [-DatabaseName <String>] [-ServiceGroupName <String>] [-ScriptType <ScriptTypes>] [-LocalDatabase] [-Sid <String>] [-DatabaseRights <String>] [-AzureDatabase] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Gets SQL scripts that can be used to create a new Host Service database schema, add a new Host Service to an existing site, remove a Host Service from a site, or create a database server logon for a Host Service. If no Sid parameter is provided, the scripts obtained relate to the currently selected Host Service instance, otherwise the scripts relate to Host Service instance running on the machine identified by the Sid provided. When obtaining the Evict script, a Sid parameter must be supplied. The current service instance is that on the local machine, or that explicitly specified by the last usage of the -AdminAddress parameter to a Host SDK cmdlet. The service instance used to obtain the scripts does not need to be a member of a site or to have had its database connection configured. The database scripts support only Microsoft SQL Server, or SQL Server Express, and require Windows integrated authentication to be used. They can be run using SQL Server's SQLCMD utility, or by copying the script into an SQL Server Management Studio (SSMS) query window and executing the query. If using SSMS, the query must be executed in 'SMDCMD mode'. The ScriptType parameter determines which script is obtained. If ScriptType is not specified, or is FullDatabase or Database, the script contains:


* Creation of service schema

* Creation of database server logon

* Creation of database user

* Addition of database user to Host Service roles

If ScriptType is Instance, the returned script contains:


* Creation of database server logon

* Creation of database user

* Addition of database user to Host Service roles

If ScriptType is Evict, the returned script contains:


* Removal of Host Service instance from database

* Removal of database user

If ScriptType is Login, the returned script contains:


* Creation of database server logon only

If the service uses two data stores they can exist in the same database. You do not need to configure a database before using this command.


## Related Commands

* [Set-HypDBConnection](./Set-HypDBConnection/)
* [Test-HypDBConnection](./Test-HypDBConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DatabaseName | Specifies the name of the database into which the new Host service schema is to be placed, or in which it already exists. The database itself is not created by any of the script types; it must already exist before the scripts are run. | false | false |  |
| ServiceGroupName | The name of the service group to be used when creating the Citrix Host Service database schema. The service group is the collection of all Host Services that share the same database and are considered equal (i.e. any service in the same service group can be used interchangeably). | false | false |  |
| ScriptType | Specifies the type of database script returned. Available script types are:<br>-- FullDatabase<br>Creates a database schema for the Citrix Host Service in a database instance that does not already contain one. This is used when creating a new site. DatabaseName and ServiceGroupName are required parameters for this script type.<br>-- Database<br>Performs the same function as "FullDatabase".<br>-- Instance<br>Adds a Host Service instance to a database and so to the associated site. Appropriate database server logons and users are created to allow the service instance access to the required service schemas.<br>-- Evict<br>Removes a Host Service instance from the database and so from the site. All reference to the service instance is removed from the database. DatabaseName and Sid are required parameters for this script type.<br>-- Login<br>Adds a logon for the Host Service instance to a database server. This is specifically for use when configuring SQL Server mirroring where the mirror server must have appropriate logons created for all service instances in the site. | false | false |  |
| LocalDatabase | Specifies whether the database script is to be used in a database instance run on the same controller as other services in the service group. Including this parameter ensures the script creates only the required permissions for local services to access the database schema for Host services. If this parameter is specified inappropriately, the service instance will not be able to connect to the database. | false | false |  |
| Sid | Specifies the SID of the controller on which the Host Service instance to remove from the database is running (only valid for a script type of Evict). | false | true (ByValue) | None |
| DatabaseRights | Specifies the right the database script should expect to be run under.  Available rights are:<br>-- Mixed<br>Creates a database schema which uses all rights.<br>-- SysAdmin<br>Creates a database schema which does the minimum with the SysAdmin (sa) rights.<br>-- DbOwner<br>Creates a database schema which only needs Database Owner (dbo) rights. This script expects to be used after the SysAdmin script has been run. | false | false | Mixed |
| AzureDatabase | Specifies that the generated schema must be compatible with Azure SQL limits, including not generating code for logins. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### System.String
A string containing the required SQL script for application to a database.
## Notes
The scripts returned support Microsoft SQL Server Express Edition, Microsoft SQL Server Standard Edition, and Microsoft SQL Server Enterprise Edition databases only, and are generated on the assumption that integrated authentication will be used.<br>    If the ScriptType parameter is not included or set to 'FullDatabase' or 'Database', the full database script is returned, which will:<br>        Create the database schema.<br>        Create the user and the role (providing the schema does not already exist).<br>        Create the logon (providing the schema does not already exist).<br>    If the ScriptType parameter is set to 'Instance', the script will:<br>        Create the user and the role (providing the schema does not already exist).<br>        Create the logon (providing the schema does not already exist) and associate it with a user.<br>    If the ScriptType parameter is set to 'Login', the script will:<br>        Create the logon (providing the schema does not already exist) and associate it with a pre-existing user of the same name.<br>    If the LocalDatabase parameter is included, the NetworkService account will be added to the list of accounts permitted to access the database.  This is required only if the database is run on a controller.<br>    If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    GetSchemasFailed<br>        The database schema could not be found.<br>    ActiveDirectoryAccountResolutionFailed<br>        The specified Active Directory account or Group could not be found.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-HypDBSchema -DatabaseName MySiteDB -ServiceGroupName  MyServiceGroup > C:\HostSchema.sql
```
#### Description
Gets a script to create the full database schema for the Citrix Host Service and copies it to a file called "C:\\HostSchema.sql"&lt;br&gt;This script can be used to create the service schema in a database with name "MySiteDB", which must already exist, and must not already contain a Host service schema.
### Example 2
```
C:\PS>Get-HypDBSchema -DatabaseName MySiteDB -ScriptType Login > C:\HostLogins.sql
```
#### Description
Gets a script to create the appropriate database server logon for the Host service. This can be used when configuring a mirror server for use.
