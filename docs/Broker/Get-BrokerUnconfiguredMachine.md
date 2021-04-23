
# Get-Brokerunconfiguredmachine
Gets machines that have registered but are not yet configured in this site.
## Syntax
```
Get-BrokerUnconfiguredMachine -SID <String> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerUnconfiguredMachine [[-MachineName] <String>] [-AgentVersion <String>] [-ControllerDNSName <String>] [-CurrentlyRegistered <Boolean>] [-DNSName <String>] [-FunctionalLevel <FunctionalLevel>] [-LastDeregistrationTime <DateTime>] [-OSType <String>] [-OSVersion <String>] [-SessionSupport <SessionSupport>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Retrieve machines matching the specified criteria, where the machine has or was previously registered with a controller in the site, but the machine has not yet been configured to be part of the site. If no parameters are specified, this cmdlet enumerates all such machines that are currently registered.

See about\_Broker\_Filtering for information about advanced filtering options, and about\_Broker\_Machines for background information about machines.


### Brokerunconfiguredmachine Object
An unconfigured machine is a machine that has registered with the site but is not configured in either a desktop group or a catalog.


  * AgentVersion (System.String) Version of the Citrix Virtual Delivery Agent (VDA) installed on the unconfigured machine.

  * ControllerDNSName (System.String) The DNS name of the controller that the unconfigured machine is registered with. This property's value is null for machines that are no longer registered.

  * CurrentlyRegistered (System.Boolean) True if the unconfigured machine is currently registered with the site, or false if the unconfigured machine is no longer registered with the site (but was registered at some point in the past).

  * DNSName (System.String) The DNS name of the unconfigured machine.

  * FunctionalLevel (Citrix.Broker.Admin.SDK.FunctionalLevel?) The functional level of the unconfigured machine. This is determined by the version of the Citrix VDA software installed on the machine.

  * LastDeregistrationTime (System.DateTime?) The time when the unconfigured machine last deregistered with the Citrix Broker Service.

  * MachineName (System.String) The machine name of the unconfigured machine in the form domain\\machine.

  * OSType (System.String) The type of operating system installed on the unconfigured machine.

  * OSVersion (System.String) The version of the operating sysetem installed on the unconfigured machine.

  * SessionSupport (Citrix.Broker.Admin.SDK.SessionSupport?) The session support of the unconfigured machine. Valid values are: SingleSession, MultiSession

  * SID (System.String) Security identifier of the unconfigured machine.


## Related Commands

* [Get-BrokerMachine](./Get-BrokerMachine/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| SID | Gets machines by their machine SID. | true | false |  |
| MachineName | Gets machines by their machine name (in the form domain\\machine). | false | false |  |
| AgentVersion | Gets machines with a specific Virtual Desktop Agent version. | false | false |  |
| ControllerDNSName | Gets machines by the DNS name of the controller they are registered with. | false | false |  |
| CurrentlyRegistered | Gets machines by whether they are currently registered with the site. If there is no CurrentlyRegistered filter, then the default is to return unconfigured machines that are currently registered. | false | false |  |
| DNSName | Gets machines by their DNS name. | false | false |  |
| FunctionalLevel | Gets machines with a specific FunctionalLevel.<br>Valid values are L5, L7, L7\_6, L7\_7, L7\_8, L7\_9, L7\_20, L7\_25 | false | false |  |
| LastDeregistrationTime | Gets machines by the time that they were last deregistered. | false | false |  |
| OSType | Gets machines by the type of operating system they are running. | false | false |  |
| OSVersion | Gets machines by the version of the operating system they are running. | false | false |  |
| SessionSupport | Gets machines that have the specified session capability. Values can be:<br>o SingleSession - Single-session only machine.<br>o MultiSession  - Multi-session capable machine. | false | false |  |
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

### Citrix.Broker.Admin.Sdk.Unconfiguredmachine
Get-BrokerUnconfiguredMachine returns an object for each matching machine
## Notes
It is generally better to compare dates and times using -Filter and relative comparisons. See about\_Broker\_Filtering and the examples in this topic for more information.
## Examples

### Example 1
```
C:\PS> Get-BrokerUnconfiguredMachine -Filter { ControllerDNSName -eq 'Controller1.domain.com' -and OSType -eq 'Windows XP Service Pack 3' }
```
#### Description
This command returns all unconfigured XP SP3 machines which are registered with the controller called 'Controller1.domain.com'.
### Example 2
```
C:\PS> Get-BrokerUnconfiguredMachine -CurrentlyRegistered $false
```
#### Description
This command returns all unconfigured machines which have registered with the site in the past, but which are not registered at present.
### Example 3
```
C:\PS> Get-BrokerUnconfiguredMachine -Filter { CurrentlyRegistered -eq $true -or CurrentlyRegistered -eq $false }
```
#### Description
This command returns all unconfigured machines which are currently registered with the site or which have registered with the site in the past.
