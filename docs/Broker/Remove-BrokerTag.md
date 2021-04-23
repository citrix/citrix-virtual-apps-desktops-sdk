
# Remove-Brokertag
Removes tag to object associations or deletes tags from the site altogether.
## Syntax
```
Remove-BrokerTag [-Tags] <Tag[]> [-AllApplications] [-AllApplicationGroups] [-AllDesktops] [-AllDesktopGroups] [-AllCatalogs] [-AllMachines] [-AllObjects] [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Catalog <Catalog>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerTag [-InputObject] <Tag[]> [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Catalog <Catalog>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Remove-BrokerTag [-Name] <String> [-Application <Application>] [-ApplicationGroup <ApplicationGroup>] [-Catalog <Catalog>] [-Desktop <Desktop>] [-DesktopGroup <DesktopGroup>] [-Machine <Machine>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Removes the association between tags and objects within the site, or deletes tags from the site altogether.

To remove an association, supply one of the Application, Machine, Desktop or DesktopGroup parameters.

To delete a tag entirely, together with any associations between the tag and other objects in the site, specify the tag without any associated object parameter.


## Related Commands

* [Add-BrokerTag](./Add-BrokerTag/)
* [Get-BrokerTag](./Get-BrokerTag/)
* [New-BrokerTag](./New-BrokerTag/)
* [Rename-BrokerTag](./Rename-BrokerTag/)
* [Set-BrokerTag](./Set-BrokerTag/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Tags | Specifies one or more tag objects. | true | true (ByValue) |  |
| InputObject | Specifies one or more tag objects. | true | true (ByValue) |  |
| Name | Specifies a tag by name. | true | true (ByPropertyName) |  |
| AllApplications | Remove the specified tags from all applications. | false | false |  |
| AllApplicationGroups | Remove the specified tags from all application groups. | false | false |  |
| AllDesktops | Remove the specified tags from all desktops. | false | false |  |
| AllDesktopGroups | Remove the specified tags from all desktop groups. | false | false |  |
| AllCatalogs | Remove the specified tags from all catalogs. | false | false |  |
| AllMachines | Remove the specified tags from all machines. | false | false |  |
| AllObjects | Remove the specified tags from all objects. | false | false |  |
| Application | Removes the association between the given tag and application. | false | true (ByValue) |  |
| ApplicationGroup | Removes the association between the given tag and application group. | false | true (ByValue) |  |
| Catalog | Removes the association between the given tag and the catalog group. | false | true (ByValue) |  |
| Desktop | Removes the association between the given tag and desktop. | false | true (ByValue) |  |
| DesktopGroup | Removes the association between the given tag and desktop group. | false | true (ByValue) |  |
| Machine | Removes the association between the given tag and machine. | false | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Tag
Tags may be specified through pipeline input.
## Return Values

### None

## Examples

### Example 1
```
C:\PS> Remove-BrokerTag $tag -Machine $machine
```
#### Description
Removes the association between a tag and a desktop. The tag itself continues to exist in the site.
### Example 2
```
C:\PS> Remove-BrokerTag $tag
```
#### Description
Deletes the tag from the site also removing any associations that may exist between the tag and other objects.
