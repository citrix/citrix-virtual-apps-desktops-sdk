
# Rename-Brokerdesktopgroup
Renames a desktop group.
## Syntax
```
Rename-BrokerDesktopGroup [-InputObject] <DesktopGroup[]> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Rename-BrokerDesktopGroup [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Rename-BrokerDesktopGroup cmdlet changes the name of a desktop group. A desktop group cannot have the same name as another desktop group.


## Related Commands

* [Get-BrokerDesktopGroup](./Get-BrokerDesktopGroup/)
* [New-BrokerDesktopGroup](./New-BrokerDesktopGroup/)
* [Set-BrokerDesktopGroup](./Set-BrokerDesktopGroup/)
* [Remove-BrokerDesktopGroup](./Remove-BrokerDesktopGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the desktop group to rename. | true | true (ByValue) | null |
| Name | Specifies the name of the desktop group to rename. | true | true (ByPropertyName) | null |
| NewName | Specifies the new name that the desktop group will have. | true | false |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Desktopgroup
You can pipe desktop groups to Rename-BrokerDesktopGroup.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Desktopgroup
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.DesktopGroup object.
## Notes
Renaming a desktop group does not alter its published name. If you need to change the name with which this desktop group appears to end-users, set a new value for the PublishedName property using the Set-BrokerDesktopGroup cmdlet.
## Examples

### Example 1
```
C:\PS> Rename-BrokerDesktopGroup -Name "Old Name" -NewName "New Name"
```
#### Description
Renames desktop group with the name "Old Name" to "New Name".
### Example 2
```
C:\PS> Get-BrokerDesktopGroup -Uid 1 | Rename-BrokerDesktopGroup -NewName "New Name" -PassThru
```
#### Description
Renames desktop group with the Uid 1 to "New Name", showing the result.
