
# Set-Configservice
Associate a Service with a Zone.
## Syntax
```
Set-ConfigService [-InputObject] <Service[]> [-Zone] <Zone> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ConfigService [-Uid] <Int32[]> [-Zone] <Zone> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Set-ConfigService [-MachineName] <String[]> [-Zone] <Zone> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet is used to change the association between Services (referred also as Controllers) and Zones. A Service can be associated with only one Zone. By default, all services are assigned to the primary Zone.


## Related Commands

* [Get-ConfigService](./Get-ConfigService/)
* [Get-ConfigZone](./Get-ConfigZone/)
* [New-ConfigZone](./New-ConfigZone/)
* [Set-ConfigSite](./Set-ConfigSite/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The service to associate with a Zone.<br>The service can be referenced by Service object, Machine Name, Machine DNS Name, SID or UID. | true | true (ByValue) |  |
| Uid | Allows specifiying Services by the Service Uid | true | true (ByPropertyName) |  |
| MachineName | Allows specifiying Services by the Machine Name | true | true (ByPropertyName) |  |
| Zone | Specifies the target Zone.<br>Zone can be referenced by Zone object, Name or UID. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Fma.Sdk.Commoncmdlets.Service
You can pipe the Services to be associated with the Zone.
## Return Values

### None

## Notes
For historical reasons Service is also referred as Controller in FMA services.
## Examples

### Example 1
```
C:\PS> Set-ConfigService -InputObject "S-1-5-21-3384143951-2794580461-1950386216-8227" -Zone "London"
```
#### Description
Associate a Service identified by SID with a Zone identified by name.
