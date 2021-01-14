
# Rename-Configzone
Rename a zone.
## Syntax
```
Rename-ConfigZone [-InputObject] <Zone> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Rename-ConfigZone [-Uid] <Guid> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Rename-ConfigZone [-Name] <String> [-NewName] <String> [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet renames a zone.

All zone names must be unique.


## Related Commands

* [New-ConfigZone](./New-ConfigZone/)
* [Set-ConfigZone](./Set-ConfigZone/)
* [Get-ConfigZone](./Get-ConfigZone/)
* [Remove-ConfigZone](./Remove-ConfigZone/)
* [Set-ConfigSite](./Set-ConfigSite/)
* [Set-ConfigService](./Set-ConfigService/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the zone to rename (by zone object). | true | true (ByValue) |  |
| Uid | Specifies the zone to rename (by Uid). | true | true (ByPropertyName) |  |
| Name | Specifies the zone to rename (by name). | true | true (ByPropertyName) |  |
| NewName | Specifies the new name of the zone. | true | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Configuration.Sdk.Zone
You can pipe the zone to be renamed into this command.
## Return Values

### None Or Citrix.Configuration.Sdk.Zone
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the zone with new name.
## Examples

### Example 1
```
C:\PS> Rename-ConfigZone -Name 'New York' -NewName 'Manhattan'
```
#### Description
Renames the 'New York' zone to 'Manhattan'.
