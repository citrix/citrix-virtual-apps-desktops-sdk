
# Get-Brokergpofilter
Gets GPO filters for a policy.
## Syntax
```
Get-BrokerGpoFilter -FilterGuid <Guid> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerGpoFilter [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieve GPO filters that meet certain criteria.


### Brokergpofilter Object
A GPO filter specifies how the policy should be applied based on the properties of a user session and/or the VDA hosting the session.


  * FilterData (System.String) Filter data.

  * FilterGuid (System.Guid) The ID of the filter.

  * FilterName (System.String) The name of the filter.

  * FilterType (System.String) The type of the filter.

  * PolicyGuid (System.Guid) The ID of the policy that owns the filter.


## Related Commands

* [New-BrokerGpoFilter](./New-BrokerGpoFilter/)
* [Set-BrokerGpoFilter](./Set-BrokerGpoFilter/)
* [Remove-BrokerGpoFilter](./Remove-BrokerGpoFilter/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| FilterGuid | Gets specified filter. If this parameter is not specified, all filters that belong to the policy are returned. | true | false |  |
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

### Citrix.Broker.Admin.Sdk.Gpofilter
Get-BrokerGpoFilter returns an object for each matching GPO filter object.
## Examples

### Example 1
```
C:\PS> Get-BrokerGpoFilter -PolicyGuid {12345678-...}
```
#### Description
Gets the filters defined for a policy.
