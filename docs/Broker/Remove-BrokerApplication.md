
# Remove-Brokerapplication
Deletes one or more applications, or an association of an application.
## Syntax
```
Remove-BrokerApplication [-InputObject] <Application[]> [-Force] [-ApplicationGroup <ApplicationGroup>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerApplication [-Name] <String> [-Force] [-ApplicationGroup <ApplicationGroup>] [-DesktopGroup <DesktopGroup>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Remove-BrokerApplication cmdlet deletes one or more applications, or you can use it to delete just the association of an application to a desktop group or application group.

Its usage dictates the behavior of the cmdlet. If only the application is specified as a parameter, then the cmdlet deletes the application. It also deletes any associations this application has with other objects, such as with access policy rules or desktop groups. More specifically, when an application is deleted the following happens:

* The association to any desktop groups is removed.
* The association to any application groups is removed.
* The association to any tags is removed.
* Any configured file-type association objects for this application are deleted.
* The association to any user accounts is removed.
* The association to any access session conditions is removed.
* The access policy rule object for this application, if one existed, is deleted.
* Finally, the application object itself is deleted.

Note that if the application is in use by a user then the application cannot be deleted.

If more than just the application is supplied as a parameter to the cmdlet (for instance, if a DesktopGroup object is also specified) then the application is not deleted. Instead, only the association from the application to that desktop group is removed.


## Related Commands

* [New-BrokerApplication](./New-BrokerApplication/)
* [Add-BrokerApplication](./Add-BrokerApplication/)
* [Get-BrokerApplication](./Get-BrokerApplication/)
* [Rename-BrokerApplication](./Rename-BrokerApplication/)
* [Move-BrokerApplication](./Move-BrokerApplication/)
* [Set-BrokerApplication](./Set-BrokerApplication/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the applications to delete. The Uid can also be substituted for the application objects. | true | true (ByValue) |  |
| Name | Specifies the name of the application to remove. | true | true (ByPropertyName) |  |
| Force | Remove application even if it's in use. Removing an application that is currently in use, can potentially leave an application session containing no applications. If all the applications that are currently active in a disconnected application session are removed, the user will be unable to reconnect to the session. Forcing removal of an in-use application does not impact the actual session itself. | false | false | false |
| ApplicationGroup | Specifies the application group that this application should no longer be associated with. The Uid or Name can also be substituted for the application group object. | false | true (ByValue) |  |
| DesktopGroup | Specifies the desktop group that this application should no longer be associated with. The Uid or Name can also be substituted for the desktop group object. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Application
The application objects can be specified as input.
## Return Values

### None
This cmdlet does not return any output.
## Examples

### Example 1
```
C:\PS> Remove-BrokerApplication "Notepad"
```
#### Description
This command deletes the application that has a BrowserName of "Notepad".
### Example 2
```
C:\PS> $app = Get-BrokerApplication -BrowserName "Notepad"

          C:\PS> $group = Get-BrokerDesktopGroup -Name "Private DesktopGroup"

          C:\PS> Remove-BrokerApplication -InputObject $app -DesktopGroup $group
```
#### Description
This command removes the association of the desktop group that has a name of "Private DesktopGroup" from the application that has a BrowserName of "Notepad". It does not otherwise modify the application.
