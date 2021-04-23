
# Get-Brokerpowertimescheme
Gets power management time schemes for desktop groups.
## Syntax
```
Get-BrokerPowerTimeScheme [-Uid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerPowerTimeScheme [[-Name] <String>] [-DesktopGroupUid <Int32>] [-Metadata <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Finds power time schemes matching the specified search criteria. Each desktop group in the site can have a number of power time schemes associated with it, and these time schemes control how the power states of machines in the group are managed.

If no search criteria are specified all power time schemes for all desktop groups are obtained.

Each power time scheme covers one or more days of the week, and defines which hours of those days are considered peak times and which are off-peak times. In addition, the time scheme defines a pool size value for each hour of the day for the days of the week covered by the time scheme. No one desktop group can be associated with two or more time schemes that cover the same day of the week.

For any day of the week not covered by any power time scheme, it is assumed that all hours are off-peak and no pool size management is required for any of the hours.

PeakHours is deprecated, and PeakHalfHours should be used instead.

PoolSize is deprecated, and PoolSizeHalfHours should be used instead.

For more information about the power policy mechanism and pool size management, see 'help about\_Broker\_PowerManagement'.


### Brokerpowertimescheme Object
The BrokerPowerTimeScheme object represents a power time scheme, defining peak/off-peak hours and idle pool sizes for desktop groups. It contains the following properties:


  * DaysOfWeek (Citrix.Broker.Admin.SDK.TimeSchemeDays) The days of the week for which this scheme applies to (Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Weekdays, Weekend).

  * DesktopGroupUid (System.Int32) The desktop group that this time scheme is for.

  * DisplayName (System.String) The name of this time scheme, as displayed in the Studio console.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this power time scheme.

  * Name (System.String) The unique name of this time scheme.

  * PeakHalfHours (System.Boolean\[\]) A set of 48 boolean flag values, one for each hour half of the day. The first value in the array relates to midnight to 00:29, the next one to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. If the flag is \$true it means that the associated half hour of the day is considered a peak time; if \$false it means that it is considered off-peak.

  * PeakHours (System.Boolean\[\]) A set of 24 boolean flag values, one for each hour of the day. The first value in the array relates to midnight to 00:59, the next one to 1 AM to 01:59 and so on, with the last array element relating to 11 PM to 11:59. If the flag is \$true it means that the associated hour of the day is considered a peak time; if it is \$false it means that it is considered off-peak.

  * PoolSize (System.Int32\[\]) For single-session desktop groups, a set of 24 integer values, one for each hour of the day. The first value in the array relates to midnight to 00:59, the next one to 1 AM to 01:59 and so on, with the last array element relating to 11 PM to 11:59. For multi-session desktop groups, a set of 48 integer values, one for each half hour of the day. The first value in the array relates to midnight to 00:29, the next one to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. The value defines the number of machines (either as an absolute number or a percentage of the machines in the desktop group) that are to be maintained in a running state, whether they are in use or not. A value of -1 has special meaning: pool size management does not apply during such hours.

  * PoolSizeHalfHours (System.Int32\[\]) A set of 48 integer values, one for each half hour of the day. The first value in the array relates to midnight to 00:29, the next one to 0:30 AM to 0:59 and so on, with the last array element relating to 11:30 PM to 11:59. The value defines the number of machines (either as an absolute number or a percentage of the machines in the desktop group) that are to be maintained in a running state, whether they are in use or not. A value of -1 has special meaning: pool size management does not apply during such half hours.

  * PoolUsingPercentage (System.Boolean?) A boolean flag to indicate whether the integer values in the pool size array are to be treated as absolute values (if this value is \$false) or as percentages of the number of machines in the desktop group (if this value is \$true).

  * Uid (System.Int32) Unique internal identifier of a time scheme.


## Related Commands

* [New-BrokerPowerTimeScheme](./New-BrokerPowerTimeScheme/)
* [Set-BrokerPowerTimeScheme](./Set-BrokerPowerTimeScheme/)
* [Remove-BrokerPowerTimeScheme](./Remove-BrokerPowerTimeScheme/)
* [Rename-BrokerPowerTimeScheme](./Rename-BrokerPowerTimeScheme/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the power time scheme with the specified Uid. | true | false |  |
| Name | Gets only power time schemes with the specified name. | false | false |  |
| DesktopGroupUid | Gets only the power time schemes associated with the specified desktop group. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Powertimescheme
Get-BrokerPowerTimeScheme returns all power time schemes that match the specified selection criteria.
## Examples

### Example 1
```
C:\PS> Get-BrokerPowerTimeScheme
```
#### Description
Fetches all known power time schemes for all desktop groups in the site.
### Example 2
```
C:\PS> Get-BrokerPowerTimeScheme -DesktopGroupUid ( Get-BrokerDesktopGroup 'Sales Desktops' ).Uid
```
#### Description
Fetches all the power time schemes for the desktop group called 'Sales Desktops'.
