
# Update-Brokerlocalleasecache
Flushes the local lease cache.
## Syntax
```
Update-BrokerLocalLeaseCache [-Workers] [-Applications] [-Icons] [-Desktops] [-Leases] [-LoggingId <Guid>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Removes all local cached lease data and any state information stored in the registry.


## Related Commands

* [Remove-BrokerLease](./Remove-BrokerLease/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Workers | Removes all locally cached workers on the controller. The worker cache will be repopulated from the current site database contents after a short delay. | false | false | false |
| Applications | Removes all locally cached applications on the controller. The application cache will be repopulated from the current site database contents after a short delay. | false | false | false |
| Icons | Removes all locally cached icons on the controller. The icon cache will be repopulated from the current site database contents after a short delay. | false | false | false |
| Desktops | Removes all locally cached desktops on the controller. The desktop cache will be repopulated from the current site database contents after a short delay. | false | false | false |
| Leases | Removes all locally cached leases on the controller. The lease cache will be repopulated from the current site database contents after a short delay. | false | false | false |
| LoggingId | Specifies the identifier of the high level operation that this cmdlet call forms a part of. Desktop Studio and Desktop Director typically create High Level Operations. PowerShell scripts can also wrap a series of cmdlet calls in a High Level Operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None

## Return Values

### None

## Notes
The local cache for lease and other data like worker, desktop, application and icon information is removed and will be repopulated from the current site database contents after a short delay.
## Examples

### Example 1
```
C:\PS> Update-BrokerLocalLeaseCache
```
#### Description
Flushes the local lease cache for all objects and deletes any state information stored in the registry.
### Example 2
```
C:\PS> Update-BrokerLocalLeaseCache -Workers
```
#### Description
Flushes the local lease cache for all workers and deletes any state information stored in the registry.
