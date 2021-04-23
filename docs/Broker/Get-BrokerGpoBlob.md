
# Get-Brokergpoblob
Gets GPO blobs defined in site.
## Syntax
```
Get-BrokerGpoBlob -BlobGuid <Guid> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerGpoBlob [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieve information about all GPO blobs or a specified GPO blob.


### Brokergpoblob Object
A GPO blob is a container of GPO policies. There is always a site blob, which contains all the site policies. There is also a blob that contains all the policy templates. Other blobs are private blobs used by individual components for special configurations.


  * BlobGuid (System.Guid) The ID of the configuration blob.

  * CurrentBlobChange (System.Guid?) Current change identifier of legacy blob.

  * CurrentTablesChange (System.Guid?) Current change identifier of blob.

  * Description (System.String) A short description of the blob.

  * LastBlobChange (System.Guid?) Previous change identifier of legacy blob.

  * LastTablesChange (System.Guid?) Previous change identifier of blob.

  * PolicyCount (System.Int32) Number of policies in the blob.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BlobGuid | Gets specified blob. If this parameter is not specified, all blobs are returned. | true | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Gpoblob
Get-BrokerGpoBlob returns an object for each matching GPO blob object.
## Examples

### Example 1
```
C:\PS> Get-BrokerGpoBlob
```
#### Description
Lists the blobs currently defined for the site.
