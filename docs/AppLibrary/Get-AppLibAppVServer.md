
# Get-Applibappvserver
Gets the details of an App-V Server created in the application library.
## Syntax
```
Get-AppLibAppVServer [-Uid <Int32>] [-ManagementServer <String>] [-PublishingServer <String>] [-RetrievePolicy <Boolean>] [-RetrievePackageIds <Boolean>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
The application library holds the information about App-V Servers and their associated policies


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Uid of the App-V server. | false | true (ByValue, ByPropertyName) |  |
| ManagementServer | Management Server Url of the App-V server. | false | true (ByValue, ByPropertyName) |  |
| PublishingServer | Publishing Server Url of the App-V server. | false | true (ByValue, ByPropertyName) |  |
| RetrievePolicy | A switch to indicate whether to return the servers policy data. | false | true (ByValue, ByPropertyName) |  |
| RetrievePackageIds | A switch to indicate whether to return the server package Ids. | false | true (ByValue, ByPropertyName) |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_AppLib\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_AppLib\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Appvserver
An object representing the details needed to identify an App-V server.
## Notes
Pass in the App-V server's UID to retrieve a single App-V server.<br>    Call the cmdlet without any parameters to retrieve all of the servers in the AppLibrary.
## Examples

### Example 1
```
Get-AppLibAppVServer
```
#### Description
Gets the details of all of the App-V servers in the AppLibrary.
### Example 2
```
Get-AppLibAppVServer -Uid 1
```
#### Description
Gets the details of the App-V server with Uid 1.
### Example 3
```
Get-AppLibAppVServer -Uid 1 -RetrievePolicy $true
```
#### Description
Gets the details of the App-V server with Uid 1, including it and its containing policy data.
### Example 4
```
Get-AppLibAppVServer -ManagementServer http://AppVSrv.company.local -PublishingServer http://AppVSrv.company.local:8001 -RetrievePolicy $true
```
#### Description
Gets the details of the App-V server with given Management Server and Publishing server urls, including it and its containing policy data.
