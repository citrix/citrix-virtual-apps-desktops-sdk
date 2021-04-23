
# New-Brokeruserzonepreference
Creates a zone preference for a user/group account in this site
## Syntax
```
New-BrokerUserZonePreference [-Name] <String> -HomeZoneUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

New-BrokerUserZonePreference [-SID] <String> -HomeZoneUid <Guid> [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerUserZonePreference cmdlet specifies a preferred home zone for resources launched using the specified user/group account.

Subject to the configuration of the desktop groups in use, and the availability of machines in the preferred zone, desktops and applications are launched using machines in that zone where possible.


## Related Commands

* [Get-BrokerUserZonePreference](./Get-BrokerUserZonePreference/)
* [Set-BrokerUserZonePreference](./Set-BrokerUserZonePreference/)
* [Remove-BrokerUserZonePreference](./Remove-BrokerUserZonePreference/)
* [Get-BrokerUser](./Get-BrokerUser/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Name of the user/group account with which the new home zone preference is to be associated. | true | true (ByPropertyName) |  |
| SID | SID of the user/group account with which the new home zone preference is to be associated. | true | true (ByPropertyName) |  |
| HomeZoneUid | The home zone preference to be associated with the user/group account. | true | true (ByPropertyName) |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Userzonepreference
New-BrokerUserZonePreference returns the newly created zone preference object.
## Examples

### Example 1
```
$zp = New-BrokerUserZonePreference EMEA\sales -HomeZoneUid 2E885C02-6B65-47AA-8B03-E855BE2FF7D7
```
#### Description
Sets the preferred zone for resources launched by members of the EMEA\\sales group account.
