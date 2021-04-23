
# Set-Brokeruserzonepreference
Changes the zone preference associated with a user/group account in this site
## Syntax
```
Set-BrokerUserZonePreference [-InputObject] <UserZonePreference[]> [-PassThru] [-HomeZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerUserZonePreference [-Name] <String> [-PassThru] [-HomeZoneUid <Guid>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerUserZonePreference cmdlet allows the preferred home zone for resources launched using the specified user/group account to be changed.

Subject to the configuration of the desktop groups in use, and the availability of machines in the preferred zone, desktops and applications are launched using machines in that zone where possible.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The account zone preference to be modified. | true | true (ByValue) |  |
| Name | The name of the user/group account whose home zone preference is to be changed. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| HomeZoneUid | The home zone preference to be associated with the user/group account for this site. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Userzonepreference
The account zone preference to be modified.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Userzonepreference
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.UserZonePreference object.
## Examples

### Example 1
```
Set-BrokerUserZonePreference APAC\marketing -HomeZoneUid 2E885C02-6B65-47AA-8B03-E855BE2FF7D7
```
#### Description
Changes the preferred zone for resources launched by members of the APAC\\marketing group account.
