
# New-Hypvmsnapshot
Creates a new snapshot for the specified VM item path.
## Syntax
```
New-HypVMSnapshot [-LiteralPath] <String> [-SnapshotName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [[-SnapshotDescription] <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to create a new snapshot of a virtual machine, for a given Host Service provider path to a VM. The resulting snapshot can then be used for operations that require a snapshot to work.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| LiteralPath | Specifies the path within a hosting unit provider to the virtual machine item for which to create a new snapshot. The path specified must be in one of the following formats: &lt;drive&gt;:\\Connections\\&lt;Connection Name&gt;\\&lt;Item Path of VM object&gt; or  &lt;drive&gt;:\\Connections\\{&lt;connection Uid&gt;\\&lt;Item Path of VM object&gt;} or &lt;drive&gt;:\\HostingUnits\\&lt;HostingUnit Name&gt;\\&lt;Item Path of VM object&gt; or  &lt;drive&gt;:\\HostingUnits\\{&lt;hostingUnit Uid&gt;\\&lt;Item Path of VM object&gt;} | true | true (ByValue) |  |
| SnapshotName | The name of the new snapshot. This is visible in the hypervisor management console. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |
| SnapshotDescription | The description to add to the snapshot. This is visible in the hypervisor management console. | false | false |  |

## Input Type

### System.String<br>    You Can Pipe A String That Contains A Path To Get-Hypconfigurationdataforitem

## Return Values

### System.String.
The provider path to the newly created snapshot.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    InputHypervisorItemPathInvalid<br>    The path provided is not to an item in a sub-directory of a connection item or a hosting unit item.<br>    InvalidHypervisorItemPath<br>    No item exists with the specified path.<br>    InvalidHypervisorItem<br>    The item specified by the path exists, but is not a VM Item.<br>    SnapshotNameAlreadyInUse<br>    The specified name is already in use and will cause a name resolution clash.<br>    FailedToCreateSnapshot<br>    The snapshot creation process failed.<br>    HypervisorInMaintenanceMode<br>    The hypervisor is in maintenance mode.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.<br>    SnapshotChainTooLong<br>    Snapshot creation failed. Snapshot chain is too long.<br>    SnapshotCreationNotAuthorized<br>    Snapshot creation failed. User not authorized to create snapshots.
## Examples

### Example 1
```
C:\PS>New-HypVMSnapshot -LiteralPath XDHyp:\Connections\MyConnection\MyVm.vm -SnapshotName "New snapshot" -SnapshotDescription "Example snapshot"

                     XDHyp:\Connections\MyConnection\MyVm.vm\New snapshot.snapshot
```
#### Description
This command creates a snapshot of a VM called 'MyVm.vm' within a hypervisor connection called 'MyConnection'.
