
# Get-Adminservice
Gets the service record entries for the DelegatedAdmin Service.
## Syntax
```
Get-AdminService [-Metadata <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns instances of the DelegatedAdmin Service that the service publishes.  The service records contain account security identifier information that can be used to remove each service from the database.

A database connection for the service is required to use this command.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Admin\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_Admin\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Delegatedadmin.Sdk.Service
The Get-AdminServiceInstance command returns an object containing the following properties.<br>Uid &lt;Integer&gt;<br>    Specifies the unique identifier for the service in the group.  The unique identifier is an index number.<br>ServiceHostId &lt;Guid&gt;<br>    Specifies the unique identifier for the service instance.<br>DNSName &lt;String&gt;<br>    Specifies the domain name of the host on which the service runs.<br>MachineName &lt;String&gt;<br>    Specifies the short name of the host on which the service runs.<br>CurrentState &lt;Citrix.Fma.Sdk.ServiceCore.ServiceState&gt;<br>    Specifies whether the service is running, started but inactive, stopped, or failed.<br>LastStartTime &lt;DateTime&gt;<br>    Specifies the date and time at which the service was last restarted.<br>LastActivityTime &lt;DateTime&gt;<br>    Specifies the date and time at which the service was last stopped or restarted.<br>OSType<br>    Specifies the operating system installed on the host on which the service runs.<br>OSVersion<br>    Specifies the version of the operating system installed on the host on which the service runs.<br>ServiceVersion<br>    Specifies the version number of the service instance.  The version number is a string that reflects the full build version of the service.<br>DatabaseUserName &lt;string&gt;<br>    Specifies for the service instance the Active Directory account name with permissions to access the database.  This will be either the machine account or, if the database is running on a controller, the NetworkService account.<br>Sid &lt;string&gt;<br>    Specifies the Active Directory account security identifier for the machine on which the service instance is running.<br>ActiveSiteServices &lt;string\[\]&gt;<br>    Specifies the names of active site services currently running in the service. Site services are components that perform long-running background processing in some services. This field is empty for services that do not contain site services.
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        One of the specified objects was not found.<br>    PartialData<br>         Only a subset of the available data was returned.<br>    InvalidFilter<br>        A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    CouldNotQueryDatabase<br>         The query required to get the database was not defined.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-AdminService

Uid                : 1

ServiceHostId      : aef6f464-f1ee-4042-a523-66982e0cecd0

DNSName            : MyServer.company.com

MachineName        : MYSERVER

CurrentState       : On

LastStartTime      : 04/04/2011 15:25:38

LastActivityTime   : 04/04/2011 15:33:39

OSType             : Win32NT

OSVersion          : 6.1.7600.0

ServiceVersion     : 5.1.0.0

DatabaseUserName   : NT AUTHORITY\NETWORK SERVICE

SID                : S-1-5-21-2316621082-1546847349-2782505528-1165

ActiveSiteServices : {MySiteService1, MySiteService2...}
```
#### Description
Get all the instances of the DelegatedAdmin Service running in the current service group.
