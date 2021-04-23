
# Get-Hypvmmacaddress
Retrieves a list the MAC addresses for the VMs in the specified connection.
## Syntax
```
Get-HypVMMacAddress [-LiteralPath] <String> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to obtain a list of MAC addresses of all the virtual machines in the specified connection.


## Related Commands

* [Get-Item](./Get-Item/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | The path to a connection item in the hosting provider.  Paths to anything other than a connection item will result in an error being returned. The path can be provided as either &lt;drive&gt;:\\connections\\&lt;Connection Name&gt; or &lt;drive:&gt;\\connections\\{&lt;Connection Uid&gt;} | true | true (ByValue) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### System.String<br>    You Can Pipe A String That Contains A Path To Get-Hypconfigurationdataforitem

## Return Values

### Citrix.Host.Sdk.Hypervisorvmobject
Get-HypVMMMacAddress returns an object containing the following properties.<br>    MacAddress &lt;string&gt; - specifies the MAC address of the VM.<br>    VMId &lt;string&gt; - specifies the identifier for the VM as defined in the hypervisor hosting it.
## Notes
The path must refer to a connection item. Hosting unit items are not valid.<br>    In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    InputConnectionsPathInvalid<br>    If the path is not provided in an expected format, an InputConnectionsPathInvalid error results.<br>    HypervisorConnectionObjectNotFound<br>    The hypervisor connection object specified cannot be found.<br>    HypervisorInMaintenanceMode<br>    The hypervisor for the connection is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-HypVMMacAddress -LiteralPath XDHyp:\Connections\MyConnection

MacAddress                              VMId

----------                              ----

52:b0:1c:ed:60:fa                       f3395d2a-a196-41c2-e37d-764acf871599

62:6f:f0:40:d5:af                       5f4457b0-cc3c-f806-8ca7-5f57e4bdf2d1

4e:a5:9f:00:b2:0c                       3115177b-85a9-d8ee-d0f9-0c7437483c09
```
#### Description
This command gets the MAC addresses for the connection called "MyConnection".
### Example 2
```
XDHyp:\Connections\MyConnection>Get-HypVMMacAddress -Path .

MacAddress                              VMId

----------                              ----

52:b0:1c:ed:60:fa                       f3395d2a-a196-41c2-e37d-764acf871599

62:6f:f0:40:d5:af                       5f4457b0-cc3c-f806-8ca7-5f57e4bdf2d1

4e:a5:9f:00:b2:0c                       3115177b-85a9-d8ee-d0f9-0c7437483c09
```
#### Description
This command gets the MAC addresses for the connection at the current directory.  The dot (.) represents the current location (not its contents).
### Example 3
```
C:\PS>Get-HypVMMacAddress -LiteralPath Xdhyp:\connections\"{268c66db-9b8c-47f6-9265-42326dbff006}"
```
#### Description
This command gets the MAC addresses for the connection that has a ConnectionUid of 268c66db-9b8c-47f6-9265-42326dbff006.
