
# Get-Brokerlease
Gets stored leases.
## Syntax
```
Get-BrokerLease [-Uid] <Int64> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerLease [[-Key] <String>] [-Expiration <DateTime>] [-LastModified <DateTime>] [-LeaseType <BrokerLeaseType>] [-OwnerSAMName <String>] [-OwnerSID <String>] [-OwnerUPN <String>] [-ZoneUid <Guid>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Gets leases filtered by specific Uid or Owner information.


### Brokerlease Object
The BrokerLease object represents a single instance of a lease. It contains the following properties:


  * Expiration (System.DateTime) The expiration time of the lease.

  * Key (System.String) The SHA1 representation of the lease key.

  * LastModified (System.DateTime) The modification time of the lease.

  * LeaseType (Citrix.Broker.Admin.SDK.BrokerLeaseType) The type of lease.

  * OwnerSAMName (System.String) The SAM name of the user associated with the lease.

  * OwnerSID (System.String) The SID of the user associated with the lease.

  * OwnerUPN (System.String) The UPN of the user associated with the lease.

  * Uid (System.Int64) The UID of the lease itself.

  * Value (System.String) The serialized lease data in XML.

  * ZoneName (System.String) Name of the Zone this resource belongs to.

  * ZoneUid (System.Guid?) Uid of the Zone this resource belongs to.


## Related Commands

* [Remove-BrokerLease](./Remove-BrokerLease/)
* [Update-BrokerLocalLeaseCache](./Update-BrokerLocalLeaseCache/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the lease specified by unique identifier. | true | false |  |
| Key | Gets only the leases matching the specified lease key pattern. | false | false |  |
| Expiration | Gets only the leases matching the specified expiration date and time. | false | false |  |
| LastModified | Gets only the leases matching the specified modified date and time. | false | false |  |
| LeaseType | Gets only leases of a specific type. Possible values Enumeration, Launch. | false | false |  |
| OwnerSAMName | Gets only the leases associated with the specified Domain\\User. | false | false |  |
| OwnerSID | Gets only the leases associated with the specified user SID. | false | false |  |
| OwnerUPN | Gets only the leases associated with the specified user UPN. | false | false |  |
| ZoneUid | Gets only the leases of resources beloning to Zone with specified Uid. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Lease
Returns an Lease object for each enumerated lease.
## Examples

### Example 1
```
C:\PS> $lease = Get-BrokerLease -Uid 1
```
#### Description
Gets the lease with internal Uid 1.
### Example 2
```
C:\PS> $leases = Get-BrokerLease -OwnerSAMName Domain\User
```
#### Description
Gets the leases associated with the specified user.
