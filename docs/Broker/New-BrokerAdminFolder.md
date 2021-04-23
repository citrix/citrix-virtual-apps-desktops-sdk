
# New-Brokeradminfolder
Creates a new admin folder.
## Syntax
```
New-BrokerAdminFolder [-FolderName] <String> [-ParentFolder <AdminFolder>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerAdminFolder cmdlet creates a new folder for organising objects for administration purposes (for example, Applications).

New-BrokerAdminFolder creates the folder object and optionally places it within an existing admin folder if required.

The following special characters are not allowed in the FolderName: \\ / ; : # . \* ? = &lt; &gt; | \[ \] ( ) " ' \`


## Related Commands

* [Get-BrokerAdminFolder](./Get-BrokerAdminFolder/)
* [Remove-BrokerAdminFolder](./Remove-BrokerAdminFolder/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| FolderName | The simple name of the new folder within its parent (if any) | true | true (ByPropertyName) |  |
| ParentFolder | The name or UID of the parent folder (if any) | false | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Depends On Parameter
Parameters can be piped by property name.
## Return Values

### Citrix.Broker.Admin.Sdk.Adminfolder
The new admin folder.
## Examples

### Example 1
```
New-BrokerAdminFolder F1
```
#### Description
Creates an admin folder called F1 under the root folder (i.e. F1\\)
### Example 2
```
New-BrokerAdminFolder F2 -AdminFolder F1\
```
#### Description
Creates an admin folder called F2 under the folder F1\\ (i.e. F1\\F2\\)
