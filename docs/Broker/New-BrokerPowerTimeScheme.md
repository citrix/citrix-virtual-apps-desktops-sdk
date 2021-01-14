
# New-Brokerpowertimescheme
Creates a new power time scheme for a desktop group.
## Syntax
```
New-BrokerPowerTimeScheme [-Name] <String> -DaysOfWeek <TimeSchemeDays> -DesktopGroupUid <Int32> [-DisplayName <String>] [-PeakHalfHours <Boolean[]>] [-PeakHours <Boolean[]>] [-PoolSize <Int32[]>] [-PoolSizeHalfHours <Int32[]>] [-PoolUsingPercentage <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The New-BrokerPowerTimeScheme cmdlet adds a new power time scheme to be associated with a desktop group. The power time scheme must relate to days of the week that are not already covered by an existing power time scheme.

Each power time scheme is associated with a particular desktop group, and covers one or more days of the week, defining which hours of those days are considered peak times and which are off-peak times. In addition, the time scheme defines a pool size value for each hour of the day for the days of the week covered by the time scheme. No one desktop group can be associated with two or more time schemes that cover the same day of the week.

See 'help about\_Broker\_PowerManagement' for a detailed description of the power policy mechanism and pool size management.


## Related Commands

* [Get-BrokerPowerTimeScheme](./Get-BrokerPowerTimeScheme/)
* [Set-BrokerPowerTimeScheme](./Set-BrokerPowerTimeScheme/)
* [Remove-BrokerPowerTimeScheme](./Remove-BrokerPowerTimeScheme/)
* [Rename-BrokerPowerTimeScheme](./Rename-BrokerPowerTimeScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Name | Specifies the administrative name of the new power time scheme. Each scheme must have a name which is unique within the site. | true | true (ByPropertyName) |  |
| DaysOfWeek | Specifies the pattern of days of the week that the power time scheme covers.<br>Valid values are (singly or a list of) Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday, Weekdays and Weekend. | true | true (ByPropertyName) |  |
| DesktopGroupUid | Specifies the desktop group that the power time scheme applies to. | true | true (ByPropertyName) |  |
| DisplayName | Specifies the name of the new power time scheme as displayed in the DesktopStudio console. Each scheme associated with a desktop group must have a display name which is unique within its desktop group, although the same display name can be used on power schemes for different desktop groups. | false | true (ByPropertyName) |  |
| PeakHalfHours | A set of 48 boolean flag values, one for each half hour of the day. The first value in the array relates to midnight to 00:29, the next one to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. If the flag is \$true it means that the associated half hour of the day is considered a peak time; if \$false it means that it is considered off-peak. | false | true (ByPropertyName) | 48 \$false values, meaning all half hours are off-peak |
| PeakHours | A set of 24 boolean flag values, one for each hour of the day. The first value in the array relates to midnight to 00:59, the next one to 1 AM to 01:59 and so on, with the last array element relating to 11 PM to 11:59. If the flag is \$true it means that the associated hour of the day is considered a peak time; if \$false it means that it is considered off-peak. | false | true (ByPropertyName) | 24 \$false values, meaning all hours are off-peak |
| PoolSize | For single-session desktop groups, a set of 24 integer values, one for each hour of the day. The first value in the array relates to midnight to 00:59, the next one to 1 AM to 01:59 and so on, with the last array element relating to 11 PM to 11:59. For multi-session desktop groups, a set of 48 integer values, one for each half hour of the day. The first value in the array relates to midnight to 00:29, the next one to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. The value defines the number of machines (either as an absolute number or a percentage of the machines in the desktop group) that are to be maintained in a running state, whether they are in use or not. A value of -1 has special meaning: pool size management does not apply during such hours. | false | true (ByPropertyName) | 24 (or 48 for multi-session desktop groups) values of '-1', meaning no pool size management is to be performed |
| PoolSizeHalfHours | A set of 48 integer values, one for each half hour of the day. The first value in the array relates to midnight to 00:29, the next one to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. The value defines the number of machines (either as an absolute number or a percentage of the machines in the desktop group) that are to be maintained in a running state, whether they are in use or not. A value of -1 has special meaning: pool size management does not apply during such half hours. | false | true (ByPropertyName) | 48 values of '-1', meaning no pool size management is to be performed |
| PoolUsingPercentage | A boolean flag to indicate whether the integer values in the pool size array are to be treated as absolute values (if this value is \$false) or as percentages of the number of machines in the desktop group (if this value is \$true). | false | true (ByPropertyName) | false |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Powertimescheme
New-BrokerPowerTimeScheme returns the newly created power time scheme.
## Examples

### Example 1
```
C:\PS> New-BrokerPowerTimeScheme -Name 'First Half Week' -DaysOfWeek Weekend,Monday,Tuesday -DesktopGroupUid 3 -PeakHalfHours (0..47 | %{ if ($_ -lt 16 -or $_ -gt 37) { $false } else { $true } } )
```
#### Description
Creates a new scheme attached to the desktop group whose UID value is 3. This new scheme covers the weekend and Monday and Tuesday, and defines 'peak' hours as 8am to 6:30pm, with all other times being 'off-peak'. No pool size values are supplied, so all size values for all the hours default to -1.
