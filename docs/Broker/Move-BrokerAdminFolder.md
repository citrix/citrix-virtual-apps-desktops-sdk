
# Move-Brokeradminfolder
Moves a folder to another place in the hierarchy, optionally renaming it
## Syntax
```
Move-BrokerAdminFolder [-InputObject] <AdminFolder[]> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Move-BrokerAdminFolder [-Name] <String> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Move-BrokerAdminFolder cmdlet moves a folder for organising objects for administration purposes (for example, Applications) to another position in the hierarchy.

The following special characters are not allowed in the new FolderName: \\ / ; : # . \* ? = &lt; &gt; | \[ \] ( ) " ' \`


## Related Commands

* [Get-BrokerAdminFolder](./Get-BrokerAdminFolder/)
* [New-BrokerAdminFolder](./New-BrokerAdminFolder/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The folder(s) to be moved | true | true (ByValue) |  |
| Name | A pattern matching the names of folders to be moved | true | true (ByPropertyName) |  |
| Destination | The destination folder the folder being moved should end up in | true | false |  |
| NewName | The name the new folder should have in the destination folder | false | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Depends On Parameter
Parameters can be piped by property name.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Adminfolder
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.AdminFolder object.
## Examples

### Example 1
```
Move-BrokerAdminFolder F1\XXX\ F2\
```
#### Description
Moves the folder called XXX within the folder F1\\ to a new home in F2\\
### Example 2
```
Move-BrokerAdminFolder F1\XXX\ F2\ -NewName YYY
```
#### Description
Moves the folder called XXX within the folder F1\\ to a new home in F2\\ renaming it to YYY in the process
