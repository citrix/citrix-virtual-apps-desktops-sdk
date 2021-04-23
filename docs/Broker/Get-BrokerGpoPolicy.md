
# Get-Brokergpopolicy
Gets GPO policies configured for this site.
## Syntax
```
Get-BrokerGpoPolicy -PolicyGuid <Guid> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerGpoPolicy [-BlobGuid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieve GPO policies matching the specified criteria. If no parameters are specified this cmdlet enumerates all GPO policies.

A GPO policy contains settings that control VDA behaviors.


### Brokergpopolicy Object
A GPO policy object is a collection of VDA configurations that control how a VDA should behave. The filters in a policy object are used to determine which VDAs are to be enforced with the specified configuration settings. Policy priorities determine how the policies should be applied together.


  * BlobGuid (System.Guid?) The ID of the configuration blob that contains this policy.

  * Description (System.String) A short description.

  * IsEnabled (System.Boolean) Specifies whether the policy is enabled. A disabled policy is not used to enforce its settings by VDAs.

  * IsReadOnly (System.Boolean) Indicates if the policy is readonly. Readonly policies are built-in objects. All user created policies are read-write.

  * PolicyGuid (System.Guid) The ID of the policy object.

  * PolicyName (System.String) The name of the policy object. Names for each policy object must be unique in a configuration blob.

  * Priority (System.Int32) Specifies the priority of this policy among all the other policies in the blob that contains this policy. The value is 1-based and the maximal value is the number of policies in the blob.


## Related Commands

* [New-BrokerGpoPolicy](./New-BrokerGpoPolicy/)
* [Set-BrokerGpoPolicy](./Set-BrokerGpoPolicy/)
* [Remove-BrokerGpoPolicy](./Remove-BrokerGpoPolicy/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| PolicyGuid | Gets only the policy object with the specified ID. | true | false |  |
| BlobGuid | Gets only the policies in the specified blob. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Gpopolicy
Get-BrokerGpoPolicy returns an object for each matching GPO policy object.
## Examples

### Example 1
```
C:\PS> Get-BrokerGpoPolicy -PolicyName 'Security settings'
```
#### Description
Finds the policy named as 'Security settings'.
### Example 2
```
C:\PS> Get-BrokerGpoPolicy
```
#### Description
Finds all policies in the default site blob.
