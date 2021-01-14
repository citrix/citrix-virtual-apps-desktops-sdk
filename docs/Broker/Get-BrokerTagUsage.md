
# Get-Brokertagusage
Produces a usage report for one or more tags.
## Syntax
```
Get-BrokerTagUsage [-TagUid] <Int32> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerTagUsage [[-TagName] <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns one BrokerTagUsage for each input tag. Each BrokerTagUsage object summarizes the tag's usage throughout the site.


### Brokertagusage Object
Each BrokerTagUsage object summarizes on the usage of a single Tag.


  * TaggedApplicationGroups (System.Int32) The number of application groups that are tagged with this tag and that are visible to the calling delegated administrator.

  * TaggedApplications (System.Int32) The number of applications that are tagged with this tag and that are visible to the calling delegated administrator.

  * TaggedCatalogs (System.Int32) The number of catalogs that are tagged with this tag and that are visible to the calling delegated administrator.

  * TaggedDesktopGroups (System.Int32) The number of desktop groups that are tagged with this tag and that are visible to the calling delegated administrator.

  * TaggedMachines (System.Int32) The number of machines that are tagged with this tag and that are visible to the calling delegated administrator.

  * TagName (System.String) The name of the Tag.

  * TagRestrictedApplicationGroups (System.Int32) The number of application groups that have this tag restriction and that are visible to the calling delegated administrator.

  * TagRestrictedAutoscale (System.Int32) The number of desktop groups that have this tag restriction

  * TagRestrictedEntitlementPolicyRules (System.Int32) The number of desktop rules in the site's entitlement policy that have this tag restriction and that are visible to the calling delegated administrator.

  * TagRestrictedRebootSchedules (System.Int32) The number of reboot schedules that have this tag restriction.

  * TagUid (System.Int32) The Uid of the Tag.

  * TagUUID (System.Guid) The UUID associated to the Tag.

  * TotalTaggedObjects (System.Int32) The total number of objects that are tagged with this tag.

  * TotalTagRestrictedObjects (System.Int32) The total number of objects that have this tag restriction.

  * UnknownTaggedObjects (System.Int32) The number of objects of all types that are tagged with this tag and that are \*not\* visible to the calling delegated administrator.

  * UnknownTagRestrictedObjects (System.Int32) The number of objects of all types that have this tag restriction and that are \*not\* visible to the calling delegated administrator.


## Related Commands

* [Get-BrokerTag](./Get-BrokerTag/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| TagUid | Report on the tag identified by TagUid. | true | false |  |
| TagName | Report on the tag identified by TagName. | false | false |  |
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
Input cannot be piped to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Tagusage
Summarizes the usage of a single tag.
## Notes
If a tag is applied to an object, but that object would not be visible to the calling delegated administrator via the corresponding Get-Broker\* cmdlet, then the object is not counted as an object of that type, but is instead reported as an 'unknown' object.<br>    For example, suppose that the caller has invoked Get-BrokerTagUsage MyTag, and that there are three desktop groups and no other objects tagged with MyTag. Two of the desktop groups are visible to the caller, but the other is not. In this case, TotalTaggedObjects is 3, TaggedDesktopGroups is 2, and UnknownTaggedObjects is 1.
## Examples

### Example 1
```
Get-BrokerTagUsage
```
#### Description
Reports on the usage of all tags in the site.
### Example 2
```
Get-BrokerTagUsage MyTag
```
#### Description
Reports on the usage of the tag MyTag.
