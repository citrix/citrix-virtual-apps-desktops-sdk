
# Rename-Brokeradminfolder
Renames a folder
## Syntax
```
Rename-BrokerAdminFolder [-InputObject] <AdminFolder[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Rename-BrokerAdminFolder [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Rename-BrokerAdminFolder cmdlet renames a folder for organising objects for administration purposes (for example, Applications).

The following special characters are not allowed in the new FolderName: \\ / ; : # . \* ? = &lt; &gt; | \[ \] ( ) " ' \`


## Related Commands

* [Get-BrokerAdminFolder](./Get-BrokerAdminFolder/)
* [New-BrokerAdminFolder](./New-BrokerAdminFolder/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The folder(s) to be renamed | true | true (ByValue) |  |
| Name | A pattern matching the names of folders to be renamed | true | true (ByPropertyName) |  |
| NewName | The name the new folder(s) should have. | true | false |  |
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
Rename-BrokerAdminFolder F1\XXX\ YYY
```
#### Description
Renames the folder called XXX within the folder F1\\ to YYY
