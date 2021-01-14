
# Get-Hypxenserveraddress
Gets all the available addresses for a XenServer hypervisor connection.
## Syntax
```
Get-HypXenServerAddress [-LiteralPath] <String> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this cmdlet to retrieve all the available hypervisor connection addresses that can be used to connect to the same XenServer pool.  When used in conjunction with Add-HypHypervisorAddress, you can easily populate a connection with all the addresses that can be used to provide full failover support for a XenServer connection.

If the addresses are https addresses, the command uses the certificates installed on the XenServers to provide suitable https addresses where possible.  Only servers that can be resolved are returned.


## Related Commands

* [Add-HypHypervisorConnectionAddress](./Add-HypHypervisorConnectionAddress/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a Host Service provider to the hypervisor connection item to which to add the address. The path specified must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;HypervisorConnectionName&gt; or  &lt;drive&gt;:\\Connections\\{HHypervisorConnection Uid&gt;} | true | true (ByValue) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.String
Get-HypXenServerAddress returns a list of strings containing the available address.
## Notes
For this to work as required with https connections, the certificates installed on the XenServers must be trusted by all controllers.  Typically this means having the root certificate for the certificate trust chain installed on all controllers.  Wildcard certificates are not supported for this operation.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    InputConnectionsPathInvalid<br>    The path provided is not to an item in a sub-directory of a hosting unit item.<br>    HypervisorConnectionNotXenServer<br>    The hypervisor connection to which the path refers is not for Citrix Hypervisor.<br>    HypervisorConnectionObjectNotFound<br>    The hypervisor connection at the path specified cannot be located.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-HypXenServerAddress -LiteralPath XDHyp:\Connections\MyConnection

https:\\myserver.com

https:\\myServer1.com
```
#### Description
Gets the available addresses for the connection "MyConnection".
### Example 2
```
c:\PS>Get-HypXenServerAddress -LiteralPath XDHyp:\Connections\MyConnection | Add-HypHypervisorConnectionAddress -LiteralPath XDHyp:\Connections\MyConnectionPath
```
#### Description
Adds all the available addresses for the XenServer pool in "MyConnection" to the hypervisor connection.
