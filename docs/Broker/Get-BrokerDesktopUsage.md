
# Get-Brokerdesktopusage
Get usage history of desktop groups.
## Syntax
```
Get-BrokerDesktopUsage [-DesktopGroupName <String>] [-DesktopGroupUid <Int32>] [-InUse <Int32>] [-Timestamp <DateTime>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns information, recorded by the broker on an hourly basis, about the number of desktops in use for each desktop group. Analyzing the historical usage records can give some guidance on usage patterns and help choosing idle pool settings.

Without parameters, Get-BrokerDesktopUsage returns the first 250 records. By using parameters, you can be more selective about the records that are returned.

To retrieve more than the default 250 records, use the -MaxRecordCount parameter.  To select data for a specific desktop group, use either the -DesktopGroupName or -DesktopGroupUid parameters.

See the examples for this cmdlet and about\_Broker\_Filtering for details of how to perform advanced filtering.


### Brokerdesktopusage Object
Desktop usage object contains information to tell how many desktops in a desktop group are in use at a given time (identified by a timestamp).


  * DesktopGroupUid (System.Int32) Uid of the desktop group that the usage data corresponds to.

  * InUse (System.Int32) Specifies how many desktop are in use at the time the timestamp corresponds to.

  * Timestamp (System.DateTime) Date and time the desktop usage information corresponds to.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| DesktopGroupName | Gets usage records for the named desktop group or for multiple desktop groups if wildcards have been specified. | false | false |  |
| DesktopGroupUid | Gets usage records for a specific desktop group. | false | false |  |
| InUse | Gets usage records where the in-use count matches the specified value. This is useful when checking for zero or when used inside a -Filter expression. | false | false |  |
| Timestamp | Gets usage records that occurred at the given time.<br>In general, Citrix recommends, using -Filter and relative comparisons. For a demonstration, see the examples. | false | false |  |
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
You cannot pipe objects to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Desktopusage
Get-BrokerDesktopUsage returns an object for each matching record.
## Notes
Desktop usage information is automatically deleted after 7 days.
## Examples

### Example 1
```
C:\PS> Get-BrokerDesktopUsage -DesktopGroupName TestGroup -MaxRecordCount 24 -SortBy '-Timestamp' | ft -a @{Name='Time';Expression={'{0:t}' -f $_.Timestamp}},InUse
```
#### Description
Returns the last 24 hours of usage information for desktop group TestGroup, formatting it as two columns labeled Time and InUse.
### Example 2
```
C:\PS> $d = Get-Date -Hour 0 -Minute 0 -Second 0

C:\PS> Get-BrokerDesktopUsage -Filter { DesktopGroupName -eq 'TestGroup' -and Timestamp -ge $d }
```
#### Description
Returns today's usage information for desktop group TestGroup.
### Example 3
```
C:\PS> $dg = Get-BrokerDesktopGroup TestGroup

C:\PS> Get-BrokerDesktopUsage -DesktopGroupUid $dg.Uid | Select Timestamp,InUse,@{Name='Percent';Expression={'{0:P0}' -f ($_.InUse / $dg.TotalDesktops)}}
```
#### Description
Retrieves the usage history for desktop group TestGroup and adds a column showing the number of desktops in that group in use, as a percentage.
