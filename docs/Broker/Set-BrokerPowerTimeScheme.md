
# Set-Brokerpowertimescheme
Modifies an existing power time scheme.
## Syntax
```
Set-BrokerPowerTimeScheme [-InputObject] <PowerTimeScheme[]> [-PassThru] [-DaysOfWeek <TimeSchemeDays>] [-DisplayName <String>] [-PeakHalfHours <Boolean[]>] [-PeakHours <Boolean[]>] [-PoolSize <Int32[]>] [-PoolSizeHalfHours <Int32[]>] [-PoolUsingPercentage <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Set-BrokerPowerTimeScheme [-Name] <String> [-PassThru] [-DaysOfWeek <TimeSchemeDays>] [-DisplayName <String>] [-PeakHalfHours <Boolean[]>] [-PeakHours <Boolean[]>] [-PoolSize <Int32[]>] [-PoolSizeHalfHours <Int32[]>] [-PoolUsingPercentage <Boolean>] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Set-BrokerPowerTimeScheme cmdlet modifies an existing time scheme.

Each power time scheme is associated with a particular desktop group, and covers one or more days of the week, defining which hours of those days are considered peak times and which are off-peak times.In addition, the time scheme defines a pool size value for each hour of the day for the days of the week covered by the time scheme. No one desktop group can be associated with two or more time schemes that cover the same day of the week.

For more information about the power policy mechanism and pool size management, see 'help about\_Broker\_PowerManagement'.


## Related Commands

* [Get-BrokerPowerTimeScheme](./Get-BrokerPowerTimeScheme/)
* [Rename-BrokerPowerTimeScheme](./Rename-BrokerPowerTimeScheme/)
* [New-BrokerPowerTimeScheme](./New-BrokerPowerTimeScheme/)
* [Remove-BrokerPowerTimeScheme](./Remove-BrokerPowerTimeScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| InputObject | The power time scheme to be changed. | true | true (ByValue) |  |
| Name | Identifies the power time scheme to be changed by name. | true | true (ByPropertyName) |  |
| PassThru | This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it returns the affected record. | false | false | False |
| DaysOfWeek | Changes the pattern of days of the week that the time scheme applies to. The pattern of days is specified as a single value or a list of values, where each value refers to either a single day or defined group of days.<br>Valid values are: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Weekend and Weekdays. | false | false |  |
| DisplayName | Changes the name that is used by the DesktopStudio console when showing the time scheme. | false | false |  |
| PeakHalfHours | A set of 48 boolean flag values, one for each hour half of the day. The first value in the array relates to midnight to 00:29, the next one to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. If the flag is \$true it means that the associated half hour of the day is considered a peak time; if \$false it means that it is considered off-peak.<br>If fewer than 48 values are supplied, the final missing values are assumed to be 'false', and if more than 48 values are supplied, only the first 48 are used. | false | false | 48 \$false values, meaning all half hours are off-peak |
| PeakHours | Changes the pattern of hours considered 'peak' vs 'off-peak' for the days covered by the time scheme. A 24-entry array of boolean truth values is expected, where the zeroth entry of the array relates to the time period between midnight and 0:59, the first relates to 1am to 1:59 and so on, with the last array element relating to 11 PM to 11:59. If the flag value is \$true it means the associated hour of the day is considered a peak time; if \$false it means that it is considered off-peak.<br>If fewer than 24 values are supplied, the final missing values are assumed to be 'false', and if more than 24 values are supplied, only the first 24 are used. | false | false |  |
| PoolSize | Changes the requested pool size of running machines at the various hours of the day (for single-session desktop groups, or half hours for multi-session) for the days covered by the time scheme.<br>For single-session desktop groups, a 24-entry array of integer values is expected, where the zeroth entry of the array relates to the time period between midnight and 0:59, the first relates to 1 AM to 1:59 and so on, with the last array element relating to 11 PM to 11:59. If fewer than 24 values are supplied, the final missing values are assumed to be -1, and if more than 24 values are supplied, only the first 24 are used.<br>For multi-session desktop groups, a 48-entry array of integer values is expected, where the zeroth entry of the array relates to the time period between midnight and 0:29, the first relates to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. If fewer than 48 values are supplied, the final missing values are assumed to be -1, and if more than 48 values are supplied, only the first 48 are used.<br>The pool size array entry values are either absolute numbers of machines that should be running or are a percentage of the machines in the desktop group that should be running during the associated hour of the day. A value of -1 in the array signifies that no management of the number of running machines should be attempted during the associated hour of the day. | false | false |  |
| PoolSizeHalfHours | Changes the requested pool size of running machines at the various half-hours of the day for the days covered by the time scheme.<br>A 48-entry array of integer values is expected, where the zeroth entry of the array relates to the time period between midnight and 0:29, the first relates to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. If fewer than 48 values are supplied, the final missing values are assumed to be -1, and if more than 48 values are supplied, only the first 48 are used.<br>The pool size array entry values are either absolute numbers of machines that should be running or are a percentage of the machines in the desktop group that should be running during the associated half hour of the day. A value of -1 in the array signifies that no management of the number of running machines should be attempted during the associated half hour of the day. | false | false |  |
| PoolUsingPercentage | Changes whether pool size values from the 'PoolSize' or 'PoolSizeHalfHours' array are evaluated as absolute numbers of running machines or as a percentage of machines in the desktop group that are to be maintained as running.<br>A value of \$true indicates that the pool size array values are percentages of total machines in the desktop group and a value of \$false indicates that the pool size array values are absolute numbers of machines to maintain as running. | false | false |  |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### Citrix.Broker.Admin.Sdk.Powertimescheme
The power time scheme to be changed.
## Return Values

### None Or Citrix.Broker.Admin.Sdk.Powertimescheme
This cmdlet does not generate any output, unless you use the PassThru parameter, in which case it generates a Citrix.Broker.Admin.SDK.PowerTimeScheme object.
## Examples

### Example 1
```
C:\PS> Set-BrokerPowerTimeScheme -Name 'Development Weekdays' -PoolSizeHalfHours ( 0..47 | %{ if ($_ -lt 16 -or $_ -gt 37) { 5 } else { 20 } } )
```
#### Description
Sets the pool size for the power time scheme named 'Development Weekdays' to be 20 for the time between 8am to 6:30pm, and 5 for other times.
