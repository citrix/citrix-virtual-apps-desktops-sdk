
# Get-Logsummary
Gets operations logged within time intervals inside a date range.
## Syntax
```
Get-LogSummary [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-IntervalSeconds <Int64>] [-GetLowLevelOperations] [-IncludeIncomplete] [-OperationType <OperationType>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The Get-LogSummary cmdlet retrieves summary counts of operations logged within time intervals inside a date range. The returned data indicates the rate at which configuration changes and activities were performed out within a time period.


## Related Commands

* [Get-LogHighLevelOperation](./Get-LogHighLevelOperation/)
* [Get-LogLowLevelOperation](./Get-LogLowLevelOperation/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| StartDateRange | Specifies the start of the summary period date range | false | false | 1900-01-01 00:00:00 |
| EndDateRange | Specifies the end of the summary period date range. | false | false | DateTime.UtcNow |
| IntervalSeconds | Specifies the size, in seconds, of each time interval required within the summary date range. If this is not specified, is null, zero or exceeds the specified date range, it defaults to the total number of seconds between EndDateRange and StartDateRange. | false | false | Total number of seconds in the EndDateRange and StartDateRange time span. |
| GetLowLevelOperations | Specifies if the cmdlet should return low level operation summary counts. | false | false | \$false - high level operations counts are returned. |
| IncludeIncomplete | Specifies if incomplete operations should be included in the returned summary counts. | false | false | \$false - incomplete operations are excluded. |
| OperationType | Specifies the type of logged operations to include. Values can be 'AdminActivity' or 'ConfigurationChange' | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Collections.Generic.Dictionary&lt;String, Int&gt;
The summary data is returned as a collection of dictionary items. The 'Key' value of each dictionary item specifies the start of the time interval within the overall summary date range. The 'Value' data in each dictionary item contains the count of operations which were started within that time interval.
## Notes
If the specified summary date range and interval period will result in more than 50,000 intervals being returned Get-LogSummary will generate an error and abort the operation.
## Examples

### Example 1
```
C:\PS> $logSummary = Get-LogSummary
```
#### Description
Get a summary of all completed high level operations. The returned log summary collection will contain a single item for the time period spanning the entire \[1900-01-01 00:00:00\]-\[UtcNow\] date range. e.g.&lt;br&gt;Key ==&gt; Value&lt;br&gt;01/01/1900 00:00:00 ==&gt; 41
### Example 2
```
C:\PS> $daily = 60\*60\*24

C:\PS> [DateTime]$startRange = "2013-02-01 14:50:39"

C:\PS> [DateTime]$endRange = $startRange.AddDays(14)

C:\PS> Get-LogSummary -StartDateRange $startRange -EndDateRange $endRange -intervalSeconds $daily
```
#### Description
Gets a summarised count of completed high level operations logged over two weeks, at daily intervals. The returned log summary collection will contain multiple items; one for each day in the summary date range. - e.g.&lt;br&gt;Key ==&gt; Value&lt;br&gt;01/02/2013 14:50:39 ==&gt;  0&lt;br&gt;02/02/2013 14:50:39 ==&gt;  4&lt;br&gt;03/02/2013 14:50:39 ==&gt; 21&lt;br&gt;04/02/2013 14:50:39 ==&gt;  0&lt;br&gt;05/02/2013 14:50:39 ==&gt;  0&lt;br&gt;06/02/2013 14:50:39 ==&gt;  0&lt;br&gt;07/02/2013 14:50:39 ==&gt;  5&lt;br&gt;08/02/2013 14:50:39 ==&gt;  0&lt;br&gt;09/02/2013 14:50:39 ==&gt;  0&lt;br&gt;10/02/2013 14:50:39 ==&gt;  0&lt;br&gt;11/02/2013 14:50:39 ==&gt;  0&lt;br&gt;12/02/2013 14:50:39 ==&gt;  7&lt;br&gt;13/02/2013 14:50:39 ==&gt;  0&lt;br&gt;14/02/2013 14:50:39 ==&gt;  0&lt;br&gt;15/02/2013 14:50:39 ==&gt; 12
### Example 3
```
C:\PS> $hourly = 60\*60

C:\PS> [DateTime]$startRange = "2013-02-03 00:00:00"

C:\PS> [DateTime]$endRange = "2013-02-03 23:59:59"

C:\PS> Get-LogSummary -StartDateRange $startRange -EndDateRange $endRange -intervalSeconds $hourly -GetLowLevelOperations
```
#### Description
Gets a summarised count of completed low level operations logged during a day, at hourly intervals.  The returned log summary collection will contain multiple items; one for each hour in the summary date range - e.g.&lt;br&gt;Key ==&gt; Value&lt;br&gt;04/03/2013 00:00:00  ==&gt; 12&lt;br&gt;04/03/2013 01:00:00  ==&gt; 10&lt;br&gt;04/03/2013 02:00:00  ==&gt;  5&lt;br&gt;.&lt;br&gt;.&lt;br&gt;.&lt;br&gt;04/03/2013 21:00:00 ==&gt; 26&lt;br&gt;04/03/2013 22:00:00 ==&gt;  0&lt;br&gt;04/03/2013 23:00:00 ==&gt;  9
