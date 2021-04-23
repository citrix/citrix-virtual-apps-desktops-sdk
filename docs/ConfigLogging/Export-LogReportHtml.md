
# Export-Logreporthtml
Exports Configuration Logging data into a HTML report.
## Syntax
```
Export-LogReportHtml -OutputDirectory <String> [-StartDateRange <DateTime>] [-EndDateRange <DateTime>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This cmdlet exports the Configuration Logging data into a HTML report. The report consists of two HTML files:

* Summary.Html - this shows summary information from the high level operation logs.
* 
Details.Html - this shows additional logging data from the low level operation and operation detail logs. Hyperlinks in summary.html allow drill-down into the associated low level logging data contained within details.html.


## Related Commands

* [Export-LogReportCsv](./Export-LogReportCsv/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| OutputDirectory | Specifies the path to a directory where the HTML report files will will be saved. | true | false |  |
| StartDateRange | Specifies the start time of the earliest operation to include. | false | false | DateTime.Min |
| EndDateRange | Specifies the end time of the latest operation to include. | false | false | DateTime.UtcNow |
| BearerToken | Specifies the bearer token assigned to the calling user. | false | false |  |
| VirtualSiteId | Specifies the virtual site id the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### 

## Examples

### Example 1
```
C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports"
```
#### Description
Export all logged operations to HTML.
### Example 2
```
C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports" -StartDateRange "2012-12-21 09:00"
```
#### Description
Export to a HTML logged operations started on or after a specified datetime..
### Example 3
```
C:\PS> Export-LogReportHtml -OutputDirectory "c:\MyReports" -StartDateRange "2012-12-21 09:00" -EndDateRange "2012-12-311 18:00"
```
#### Description
Export to HTML logged operations started and completed between a date range.
