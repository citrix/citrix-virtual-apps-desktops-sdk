
# Get-Brokerhypervisoralert
Gets hypervisor alerts recorded by the controller.
## Syntax
```
Get-BrokerHypervisorAlert -Uid <Int64> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerHypervisorAlert [-HostingServerName <String>] [-HypervisorConnectionUid <Int32>] [-Metadata <String>] [-Metric <AlertMetric>] [-Severity <AlertSeverity>] [-Time <DateTime>] [-TriggerInterval <TimeSpan>] [-TriggerLevel <Double>] [-TriggerPeriod <TimeSpan>] [-TriggerValue <Double>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerHypervisorAlert cmdlet gets alert objects reported by the hypervisors that the controller is monitoring.

Without parameters, Get-BrokerHypervisorAlert gets all of the alerts recorded. Use parameters to select which alerts are returned.

Once you have configured suitable alerts in your hypervisor, and configured the controller with your hypervisor details (see New-BrokerHypervisorConnection), the controller monitors each hypervisor for new alerts.

Four hypervisor alert metrics are recorded; these relate to the hypervisor host, not individual virtual machines:

* Cpu: Reports excessive CPU usage.
* Memory: Reports excessive memory usage.
* Network: Reports high network activity.
* Disk: Reports high disk activity.

Each alert also includes information about where and when the alert occurred, the severity of the alert (Red/Yellow), and the configuration of the triggered alert.

The following metrics are supported with these hypervisors:

* VMware ESX (Cpu, Memory, Network, Disk)
* Citrix XenServer (Cpu, Network)
* Microsoft Hyper-V (None)

### Brokerhypervisoralert Object

The BrokerHypervisorAlert represents a hypervisor alert object. It contains the following properties:


  * HostingServerName (System.String) The name of the hypervisor hosting this machine.

  * HypervisorConnectionUid (System.Int32) The Uid of the hypervisor connection that reported this alert.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this hypervisor alert.

  * Metric (Citrix.Broker.Admin.SDK.AlertMetric) The metric this alert relates to: Cpu, Memory, Network, Disk, HostConnection or HostReboot.

  * Severity (Citrix.Broker.Admin.SDK.AlertSeverity) Severity of the alert (Red or Yellow). Red is more serious than Yellow.

  * Time (System.DateTime) Time that the alert occurred.

  * TriggerInterval (System.TimeSpan?) Number of ticks (100ns) before the alert can be raised again.

  * TriggerLevel (System.Double?) Threshold level that the alert was configured to trigger at.

  * TriggerPeriod (System.TimeSpan?) Duration the value was above the trigger level.

  * TriggerValue (System.Double?) The value of the monitored metric that triggered the alert.

  * Uid (System.Int64) The unique internal identifier of this alert.


## Related Commands

* [New-BrokerHypervisorConnection](./New-BrokerHypervisorConnection/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets the hypervisor alert with the specified UID. | true | false |  |
| HostingServerName | Gets alerts for the specified hosting hypervisor server. | false | false |  |
| HypervisorConnectionUid | Gets alerts for the specified hypervisor connection. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| Metric | Gets alerts for a specified metric.<br>Valid values are: Cpu, Memory, Network and Disk. | false | false |  |
| Severity | Gets alerts with the specified severity.<br>Valid values are: Red and Yellow. | false | false |  |
| Time | Gets alerts that occurred at a specific time.<br>You can also use -Filter and relative comparisons; see the examples for more information. | false | false |  |
| TriggerInterval | Gets alerts with a specific trigger interval. This is the interval before the alert is raised again. | false | false |  |
| TriggerLevel | Gets alerts with a specific trigger threshold level. | false | false |  |
| TriggerPeriod | Gets alerts with a specific trigger period. This is the duration the threshold level was exceeded for, prior to the alert triggering. | false | false |  |
| TriggerValue | Gets the value of the monitored metric that triggered the alert. | false | false |  |
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
You cannot pipe objects to this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Hypervisoralert
Get-BrokerHypervisorAlert returns an object for each matching alert.
## Examples

### Example 1
```
C:\PS> Get-BrokerHypervisorAlert -HostingServerName TestHyp\* -Severity Red
```
#### Description
Returns all serious (Red) alerts for any hosting server with a name that starts with 'TestHyp'.
### Example 2
```
C:\PS> Get-BrokerHypervisorAlert -Filter { Metric -eq 'Cpu' -and Time -ge '-1:0' }
```
#### Description
Returns all CPU usage alerts that occurred in the last hour.
