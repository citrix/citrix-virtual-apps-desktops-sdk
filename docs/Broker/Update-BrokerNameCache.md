
# Update-Brokernamecache
Performs administrative operations on the user/group and machine name cache.
## Syntax
```
Update-BrokerNameCache [-Machines] [-Users] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Update-BrokerNameCache -Purge [-Machines] [-Users] [-UnusedFor <TimeSpan>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Triggers an immediate asynchronous refresh of the name cache, or when used with the -Purge parameter removes cache entries that are unreferenced and have been unused for a period of time.

The Broker Service maintains a cache of the names of users/groups and machines in use by the site. By default, name information is obtained periodically from Active Directory and the cache refreshed automatically.

Triggering a cache refresh with this cmdlet ensures up-to-date name information is present in the cache after user/group or machine accounts are known to have changed and you need to see those changes immediately instead of waiting for the periodic automatic refresh.

Removing (purging) entries relating to no longer used user/group or machine accounts is useful to stop requests being made to Active Directory to refresh the names relating to those items.

For users/groups, the following name information is cached: Windows name (DOMAIN\\user) User Principal Name or 'UPN' (user@upndomain) Full Name or 'Common Name' (typically a user's full name)

For machines, the following name information is cached: Windows name (DOMAIN\\machine) DNS name (machine.dnsdomain)


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Purge | Removes unused entries from the cache rather than refreshing the name data. Entries are only removed if they are not configured or referenced in any way within the site.<br>In addition, user entries are only removed if the user has not logged in for at least 90 days. Similarly machine entries are only removed if the machine has not registered with the site over the same period. The 90 day default can be overridden using the -UnusedFor parameter.<br>While removing genuinely unused cache entries is desirable to reduce the requests made to Active Directory, there is additional cost in repopulating the cache if a user/group or machine account is later used again after having been removed. Thus it is not recommended to routinely use very short intervals with -UnusedFor.<br>If a machine entry is removed from the cache and later used again, the Uid value associated with that machine changes (seen in the output of Get-BrokerMachine). | true | false |  |
| Machines | Triggers an asynchronous refresh of all cached machine name information, or with the -Purge parameter removes unused machine entries from the cache. | false | false |  |
| Users | Triggers an asynchronous refresh of all cached user/group name information, or with the -Purge parameter removes unused user/group entries from the cache. | false | false |  |
| UnusedFor | Specifies the minimum period over which user or machine cache entries must have been unused before they can be be removed with the -Purge option. | false | false | 90 days |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### None

## Notes
For some user accounts, for example, the built-in domain administrator, the UPN and/or Full Name values may not be available because they are not typically specified within Active Directory.<br>    For group accounts, UPN and Full Name values are not available because they are not applicable or not specified within Active Directory.<br>    The DNS name information for a machine is obtained from Active Directory and not from the DNS sub-system. If a machine has only recently been configured, the DNS information may not be available initially.
## Examples

### Example 1
```
C:\PS> Update-BrokerNameCache -Machines
```
#### Description
Triggers an immediate asynchronous refresh of all machine name information held within the name cache.
### Example 2
```
C:\PS> Update-BrokerNameCache -Machines -Users
```
#### Description
Triggers an immediate asynchronous refresh of all machine and user name information held within the name cache.
