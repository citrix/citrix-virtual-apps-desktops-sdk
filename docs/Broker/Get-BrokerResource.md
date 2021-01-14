
# Get-Brokerresource
Gets resources that a user can broker connections to.
## Syntax
```
Get-BrokerResource [-User] <String> [-Groups <String[]>] [-TenantId <Guid>] [-ClientName <String>] [-ClientIP <String>] [-ViaAG <Boolean>] [-SmartAccessTags <String[]>] [-AppProtectionCapable <Boolean>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieve a list of resources that a user has access to, taking into account the site access policy, configuration of desktop groups, assignments, entitlements, and applications.

What a user has access to depends on a number of attributes:

* User's name or security identifier.
* Groups that the user is a member of (names or security identifiers).
* IP address of the client the user connects from.
* Name of the client that the user connects from.
* Whether the user is connecting via Citrix Access Gateway.
* SmartAccess tags when connecting via Citrix Access Gateway.

You must always specify the user's name or security identifier, but you will not always be able to predict what some of the other values will be. By omitting these values the corresponding access checks are ignored.

Consider for example, a site configuration that uses IP address ranges to allow access to private desktop A when connecting from the local network and private desktop B when connecting from home. Running this cmdlet without specifying a client IP address would return both A and B.

The output of this cmdlet depends on the available resources:

* Assigned private desktops are returned as PrivateDesktop objects.
* Shared desktops are returned as EntitlementPolicyRule objects.
* Assign-On-First-Use desktops that have not been assigned yet are returned as AssignmentPolicyRule objects.
* Application resources produce Application objects.

If more than one type of resource is available, the output pipeline contains a mixture of the above objects, in no particular order.

Only resources accessible based on the specified parameters, and visible to the administrator running this cmdlet are returned.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| User | Gets resources given the specified user name or security identifier. | true | false |  |
| Groups | Get resources accessible given a list of group names or security identifiers. | false | false |  |
| TenantId | Specifies identity of tenant associated with the user and groups. Can only be used in multitenant sites. | false | false |  |
| ClientName | Get resources given the specified client name. | false | false |  |
| ClientIP | Get resources given the specified client IP address. | false | false |  |
| ViaAG | Gets resources given the specified ViaAG setting. | false | false |  |
| SmartAccessTags | Get resources given the specified SmartAccess tags. | false | false |  |
| AppProtectionCapable | Get Resources given the specified app protection capability of the client. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Application
Get-BrokerResource returns an Application object for each accessible application.
### Citrix.Broker.Admin.Sdk.Assignmentpolicyrule
Get-BrokerResource returns an AssignmentPolicyRule object for each accessible Assign-On-First-Use desktop.
### Citrix.Broker.Admin.Sdk.Entitlementpolicyrule
Get-BrokerResource returns an EntitlementPolicyRule object for each accessible entitlement to a shared desktop.
### Citrix.Broker.Admin.Sdk.Privatedesktop
Get-BrokerResource returns a PrivateDesktop for each accessible assigned private desktop.
## Examples

### Example 1
```
Get-BrokerResource -User MYDOMAIN\User1 -Groups MYDOMAIN\Accounts,MYDOMAIN\Managers
```
#### Description
List resources visible by User1 assuming membership of a couple of groups.
### Example 2
```
[int[]]$groups = (Get-BrokerResource -User MYDOMAIN\User1 | %{ $_.DesktopGroupUid })

Get-BrokerDesktopGroup -Filter { Uid -in $groups } -Property Uid,Name
```
#### Description
Get all of the desktop groups supporting the resources accessible by User1, outputting the uid and name of each desktop group.
