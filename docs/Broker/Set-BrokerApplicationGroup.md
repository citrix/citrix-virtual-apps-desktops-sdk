
# Set-Brokerapplicationgroup
Changes properties of application groups.
## Syntax
```
Set-BrokerApplicationGroup [-InputObject] <ApplicationGroup[]> [-PassThru] [-Description <String>] [-Enabled <Boolean>] [-RestrictToTag <String>] [-SessionSharingEnabled <Boolean>] [-SingleAppPerSession <Boolean>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerApplicationGroup [-Name] <String> [-PassThru] [-Description <String>] [-Enabled <Boolean>] [-RestrictToTag <String>] [-SessionSharingEnabled <Boolean>] [-SingleAppPerSession <Boolean>] [-UserFilterEnabled <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerApplicationGroup cmdlet changes the properties of one or more application groups. The changed properties and the new values of those properties are specified as parameters to Set-BrokerApplicationGroup.

This cmdlet cannot change the relationships of application group objects with other objects. For instance, it cannot change which users can access applications in this application group, or change which desktop groups this application group is published to. To do this, you need to remove the existing association, and then add a new association.

The following example shows how to change the desktop group that application group \$applicationGroup is associated with from \$desktopGroup1 to \$desktopGroup2: Remove-BrokerApplicationGroup \$applicationGroup -DesktopGroup \$desktopGroup1 Add-RemoveApplicationGroup \$applicationGroup -DesktopGroup \$desktopGroup2

Application groups may not be renamed using this cmdlet. To rename an application group, use Rename-BrokerApplicationGroup.


## Related Commands

* [Add-BrokerApplicationGroup](./Add-BrokerApplicationGroup/)
* [Get-BrokerApplicationGroup](./Get-BrokerApplicationGroup/)
* [New-BrokerApplicationGroup](./New-BrokerApplicationGroup/)
* [Remove-BrokerApplicationGroup](./Remove-BrokerApplicationGroup/)
* [Rename-BrokerApplicationGroup](./Rename-BrokerApplicationGroup/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the application group whose properties should be altered. Its Uid can also be substituted for the object reference. | true | true (ByValue) |  |
| Name | Alters the properties of application groups whose name matches the supplied pattern. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| Description | The new description for the application group. | false | false |  |
| Enabled | Whether the application group's applications should be launchable by end users. | false | false |  |
| RestrictToTag | Specifies the new values of the application group's tag restriction. | false | false |  |
| SessionSharingEnabled | Specifies the new value of the application group's SessionSharingEnabled flag. Please note this setting and SingleAppPerSession cannot be true at the same time. | false | false |  |
| SingleAppPerSession | Specifies whether each application launched from this application group starts in its own new session or can share an existing suitable session if present. Please note this setting and SessionSharingEnabled cannot be true at the same time. | false | false |  |
| UserFilterEnabled | Specifies the new value of the application group's UserFilterEnabled flag. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Applicationgroup
You can pipe application groups to Set-BrokerApplication.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Applicationgroup
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.ApplicationGroup object.
## Examples

### Example 1
```
C:\PS> Set-BrokerApplicationGroup 'Helpdesk Apps' -Enabled $false
```
#### Description
Prevent new instances of applications in the 'Helpdesk Apps' application group from being launched.
### Example 2
```
C:\PS> Get-BrokerApplicationGroup | Set-BrokerApplicationGroup -UserFilterEnabled $false
```
#### Description
Disable the user filter on every application group in the system. (Other access control mechanisms, such as access policy and user filters on individual applications, still apply.)
