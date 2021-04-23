
# Set-Configzone
Set the description of the zone.
## Syntax
```
Set-ConfigZone [-InputObject] <Zone[]> [-Description <String>] [-EnableHybridConnectivityForResourceLeases <Boolean>] [-ExternalUid <Guid>] [-TenantId <Guid>] [-NewUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ConfigZone [-Uid] <Guid[]> [-Description <String>] [-EnableHybridConnectivityForResourceLeases <Boolean>] [-ExternalUid <Guid>] [-TenantId <Guid>] [-NewUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ConfigZone [-Name] <String[]> [-Description <String>] [-EnableHybridConnectivityForResourceLeases <Boolean>] [-ExternalUid <Guid>] [-TenantId <Guid>] [-NewUid <Guid>] [-PassThru] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet allows you to change the description of a zone.

Controllers can be moved between zones using Set-ConfigService cmdlet. To mark zone as primary use Set-ConfigSite cmdlet.

To update the metadata associated with a zone, use the Set-ConfigZoneMetadata and Remove-ConfigZoneMetadata cmdlets.

To change the name of a zone use Rename-ConfigZone cmdlet.


## Related Commands

* [New-ConfigZone](./New-ConfigZone/)
* [Get-ConfigZone](./Get-ConfigZone/)
* [Rename-ConfigZone](./Rename-ConfigZone/)
* [Remove-ConfigZone](./Remove-ConfigZone/)
* [Set-ConfigSite](./Set-ConfigSite/)
* [Set-ConfigService](./Set-ConfigService/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | Specifies the zone to update (by zone object). | true | true (ByValue) |  |
| Uid | Specifies the zone to update (by Uid). | true | true (ByPropertyName) |  |
| Name | Specifies the zone to update (by name). | true | true (ByPropertyName) |  |
| Description | Supplies the new description. | false | false |  |
| EnableHybridConnectivityForResourceLeases | Supplies the EnableHybridConnectivityForResourceLeases property of the zone | false | false |  |
| ExternalUid | Supplies the external Uid of the zone | false | false |  |
| TenantId | Supplies the Tenant ID of the zone | false | false |  |
| NewUid | Specifies the new uid of the Zone object. | false | false |  |
| PassThru | Returns the affected record. By default, this cmdlet does not generate any output. | false | false | False |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Configuration.Sdk.Zone
You can pipe the zones to be updated into this command.
## Return Values

### None Or Citrix.Configuration.Sdk.Zone
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Zone object.
## Examples

### Example 1
```
C:\PS> Set-ConfigZone -Name 'Sydney' -Description 'Sydney branch office'
```
#### Description
Change the description of the 'Sydney' zone.
