
# Get-Brokerconnectionlog
Get entries from the site's session connection log.
## Syntax
```
Get-BrokerConnectionLog [-Uid] <Int64> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerConnectionLog [[-MachineName] <String>] [-BrokeringTime <DateTime>] [-BrokeringUserName <String>] [-BrokeringUserUPN <String>] [-ConnectionFailureReason <ConnectionFailureReason>] [-Disconnected <Boolean>] [-EndTime <DateTime>] [-EstablishmentTime <DateTime>] [-MachineDNSName <String>] [-MachineUid <Int32>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Gets connection log entries matching the specified criteria. If no parameters are specified all connection log entries are returned.

The session connection log contains entries describing each brokered connection, or reconnection, attempt to a session in the site.

Each log entry describes a single connection brokering attempt to a new or existing session within the site. A single session can have multiple entries in the connection log, for example where the end user brokers a connection to a new session, disconnects and later brokers a reconnection. Conversely, other sessions may have none (e.g. console sessions).

By default connection log entries are removed after 48 hours.

For information about advanced filtering options when using the -Filter parameter, see about\_Broker\_Filtering; for information about machines, see about\_Broker\_Machines.


### Brokerconnectionlog Object
The BrokerConnectionLog object represents a single brokered connection attempt to a new or existing session on a machine in the site. It contains the following properties:


  * BrokeringTime (System.DateTime) The time at which the connection attempt was made.

  * BrokeringUserName (System.String) The name of the user making the connection (in DOMAIN\\User format).

  * BrokeringUserUPN (System.String) The name of the user making the connection (in user@upndomain.com format).

  * ConnectionFailureReason (Citrix.Broker.Admin.SDK.ConnectionFailureReason?) The status of the connection attempt. A value of None indicates that the connection was successfully established, \$null that the attempt is still in progress, and other values indicate that the attempt failed for the specified reason.

  * Disconnected (System.Boolean?) Indicates if the connection was ended by disconnection (True), logoff or establishment failure (False), or is still active (\$null).

  * EndTime (System.DateTime?) The time at which the connection ended. If the connection ended by disconnection, the underlying machine session would still exist in a disconnected state.

  * EstablishmentTime (System.DateTime?) The time at which the connection was successfully established. The value is \$null if the connection attempt failed or is still in progress.

  * MachineDNSName (System.String) The name of the machine to which the connection was made (in machine@dnsdomain.com form).

  * MachineName (System.String) The name of the machine to which the connection was made (in DOMAIN\\Machine format).

  * MachineUid (System.Int32) The UID of the machine to which the connection was made.

  * Uid (System.Int64) The UID of the connection log entry itself.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets a specific connection log entry identified by its UID. | true | false |  |
| MachineName | Gets connection log entries for the specified machines (in DOMAIN\\Machine format). | false | false |  |
| BrokeringTime | Gets connection log entries with a specified brokering time. For more flexibility when searching on brokering time use the -Filter parameter. | false | false |  |
| BrokeringUserName | Gets connection log entries for the specified users (in DOMAIN\\User format). | false | false |  |
| BrokeringUserUPN | Gets connection log entries for the specified users (in user@upndomain.com format). | false | false |  |
| ConnectionFailureReason | Gets connection log entries which failed for the specified reason. | false | false |  |
| Disconnected | Gets connection log entries with the specified disconnection status, that is, whether the connection was disconnected, or logged-off. | false | false |  |
| EndTime | Gets connection log entries with the specified end time. For more flexibility when searching on end time use the -Filter parameter. | false | false |  |
| EstablishmentTime | Gets connection log entries with the specific establishment time. For more flexibility when searching on establishment time use the -Filter parameter. | false | false |  |
| MachineDNSName | Gets connection log entries for the specified machines (in machine@dnsdomain.com format). | false | false |  |
| MachineUid | Gets connection log entries for a specific machine identified by its UID. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Connectionlog
An entry from the connection log.
## Examples

### Example 1
```
C:\PS> $when = [DateTime]::Now - [TimeSpan]::FromMinutes(30)

C:\PS> Get-BrokerConnectionLog -Filter {BrokeringTime -gt $when} -SortBy '+MachineName,-EndTime'
```
#### Description
Gets all connection log entries for sessions brokered in the past 30 minutes, ordered first by machine name (ascending), then by session end time (descending).
