
# Get-Hypconfigurationobjectforitem
Retrieves the configuration data for an item in the Host Service provider path.  Note: For this release, only VM items are supported for this operation.
## Syntax
```
Get-HypConfigurationObjectForItem [-LiteralPath] <String> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This command provides a mechanism for retrieving extra data about an entry in the hosting unit service provider.  The referenced item must be contained within the connections directory in the provider (i.e. XDHyp:\\Connections).

This mechanism is used for obtaining data that is not required frequently and/or has a high overhead associated with its retrieval (so as to maintain the responsiveness of the provider). For this release of the PowerShell snap-in the only provider items that can be used with this operation are VM items.  For a VM this provides a mechanism to obtain the number of CPUs, the amount of Memory (in MB) and hard disk drive capacity (GB).


## Related Commands

* [Get-Item](./Get-Item/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a hosting unit provider to the item for which configuration data is to be retrieved. The path specified must be in one of the following formats; &lt;drive&gt;:\\Connections\\&lt;Connection Name&gt;\\&lt;Item Path of VM object&gt; or  &lt;drive&gt;:\\Connections\\{&lt;connection Uid&gt;\\&lt;Item Path of VM object&gt;} or &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnit Name&gt;\\&lt;Item Path of VM object&gt; or  &lt;drive&gt;:\\HostingUnits\\{&lt;hostingUnit Uid&gt;\\&lt;Item Path of VM object&gt;} | true | true (ByValue) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in will connect to.  This can be provided as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### System.String<br>    You Can Pipe A String The Contains A Path To Get-Hypconfigurationdataforitem

## Return Values

### Psobject
Get-HypConfigurationDataForItem returns a PSObject containing the properties that are appropriate for the item specified by the path.<br>    Properties for VM Item<br>    ----------------------<br>    CPUCount &lt;int&gt;<br>        Specifies the number of CPUs assigned to the VM.<br>    MemoryMB &lt;int&gt;<br>        The amount of memory allocated to the VM.<br>    HardDiskSizeGB &lt;int&gt;<br>        The capacity of the primary hard drive assigned to the VM.<br>    Network Map<br>        The networks that this Vm or Snaphot is connected to
## Notes
For this release this cmdlet only provides configuration data for VM objects in the provider.  Using a path to an item that is not a VM will result in a error.<br>    In the case of failure the following errors can be produced.<br>    Error Codes<br>    -----------<br>    InputHypervisorItemPathInvalid<br>    The path provided is not to an item in a sub directory of a connection item or a hosting unit item.<br>    InvalidHypervisorItemPath<br>    No item exists with the specified path.<br>    InvalidHypervisorItem<br>    The item specified by the path exists, but is not a VM Item.<br>    DatabaseError<br>    An error occurred in the service whilst attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed as the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service whilst attempting a database operation - communication to database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred whilst communicating with the service.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    HypervisorPermissionDenied<br>    The hypervisor login used does not provide authorization to access the data for this item.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details see the Windows event logs on the controller being used, or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-HypConfigurationDataForItem -LiteralPath XDHyp:\Connections\MyConnection\MyVm.vm

                              CpuCount                                MemoryMB                          HardDiskSizeGB

                              --------                                --------                          --------------

                                     1                                    1024                                      24
```
#### Description
This command gets the configuration properties for a VM called 'MyVm.vm' within a hypervisor connection called 'MyConnection'.
### Example 2
```
XDHyp:\HostingUnits\PS>Get-HypConfigurationDataForItem -LiteralPath .\MyVm.vm

                              CpuCount                                MemoryMB                          HardDiskSizeGB

                              --------                                --------                          --------------

                                     1                                    1024                                      24
```
#### Description
This command gets the configuration properties for a VM called 'MyVm.vm' within the current directory.  The dot (.) represents the current location (not its contents).
### Example 3
```
C:\PS>(Get-HypConfigurationDataForItem -LiteralPath XDHyp:\Connections\MyConnection\MyVm.vm).CPUCount
```
#### Description
This command gets the CPU count for a VM called 'MyVm.vm'.  The CPUCount is just one property of the VM items.  To see all properties of an item, type "(Get-HypConfigurationDataForItem &lt;ItemPath&gt;) | Get-Member".
