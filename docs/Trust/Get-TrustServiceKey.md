
# Get-Trustservicekey
Gets register ServiceKey configured for this site.
## Syntax
```
Get-TrustServiceKey [[-Uid] <Int32>] [-InstanceId <String>] [-InstanceName <String>] [-IsTrustService <Boolean>] [-LastUpdated <DateTime>] [-RotationNeeded <Boolean>] [-ServiceName <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Retrieves registered ServiceKey matching the specified criteria. If no parameters are specified, all registered ServicesKey will be returned.


## Related Commands

* [Register-TrustServiceKey](./Register-TrustServiceKey/)
* [Set-TrustServiceKeyRotation](./Set-TrustServiceKeyRotation/)
* [Unregister-TrustServiceKey](./Unregister-TrustServiceKey/)
* [Revoke-TrustPreviousServiceKey](./Revoke-TrustPreviousServiceKey/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Get ServiceKey with the specified Unique Identifier. | false | true (ByValue, ByPropertyName) |  |
| InstanceId | Get ServiceKey with the specified instance identifier. | false | false |  |
| InstanceName | Get ServiceKey with the specified instance name | false | false |  |
| IsTrustService | Get ServiceKey with the specified value of the IsTrustService flag. If true, only Service Keys for the Trust Service will be returned. | false | false |  |
| LastUpdated | Get ServiceKey where the public key was last updated at the specified time. | false | false |  |
| RotationNeeded | Get ServiceKey with the specified value of the RotationNeeded flag. If true, only ServiceKey that need to be rotated will be returned. If false, only ServiceKey where key rotation is not pending will be returned. | false | false |  |
| ServiceName | Get ServiceKey with the specified service name. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Trust\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_Trust\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Trust.Sdk.Servicekey
Get-TrustServiceKey returns an object for each matching registered Service Key.
## Examples

### Example 1
```
Get-TrustServiceKey
```
#### Description
Gets all service keys.
### Example 2
```
Get-TrustServiceKey -IsTrustService $true
```
#### Description
Gets all service keys for a Trust Service.
### Example 3
```
Get-TrustServiceKey -Filter "LastUpdated -lt '10-20-2015'" | Set-TrustServiceKeyRotation
```
#### Description
Mark all the service keys whose public key were last updated before October 20, 2015 to rotate their public keys.
### Example 4
```
Get-TrustServiceKey -Filter "LastUpdated -gt '10-20-2016'" | Revoke-TrustPreviousServiceKey
```
#### Description
Revoke the previous public key of all service keys that were updated after October 20, 2016.
