
# Move-Brokerapplication
Move a published application from one admin folder to another
## Syntax
```
Move-BrokerApplication [-InputObject] <Application[]> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Move-BrokerApplication [-Name] <String> [-Destination] <AdminFolder> [-NewName <String>] [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Move-BrokerApplication cmdlet moves a published application from one place to another in the tree of admin folders, optionally renaming it in the process (if you only want to change the name of the application for administrative purposes and not its location in the tree, use the Rename-BrokerApplication cmdlet).

The location and name of a published application in this sense is only of interest to the administrator, changes do not affect the end-user experience.


## Related Commands

* [New-BrokerApplication](./New-BrokerApplication/)
* [Add-BrokerApplication](./Add-BrokerApplication/)
* [Get-BrokerApplication](./Get-BrokerApplication/)
* [Remove-BrokerApplication](./Remove-BrokerApplication/)
* [Rename-BrokerApplication](./Rename-BrokerApplication/)
* [Set-BrokerApplication](./Set-BrokerApplication/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The application(s) to be moved | true | true (ByValue) |  |
| Name | The application(s) to be moved | true | true (ByPropertyName) |  |
| Destination | The destination location within the admin folder hierarchy | true | false |  |
| NewName | The new name of the application in its new destination | false | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Application
You can pipe applications to Move-BrokerApplication.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Application
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.Application object.
## Examples

### Example 1
```
C:\PS> Move-BrokerApplication -Name 'App1' -Destination 'F1\'
```
#### Description
Moves the application in the root folder called "App1" to the folder "F1\\".
### Example 2
```
C:\PS> Move-BrokerApplication 'F1\App1' 'F2\' -NewName 'Application1'
```
#### Description
Moves the application in folder "F1" called "App1" to the folder "F2\\", renaming it to "Application1" in the process.
