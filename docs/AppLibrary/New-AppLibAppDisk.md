
# New-Applibappdisk
Creates a new AppDisk.
## Syntax
```
New-AppLibAppDisk [-AppDiskName] <String> -HostingUnitName <String> -DiskSizeMB <Int32> -PreparationMachine <String> [-Scope <String[]>] [-AppDiskDescription <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AppLibAppDisk [-AppDiskName] <String> -HostingUnitUid <Guid> -DiskSizeMB <Int32> -PreparationMachine <String> [-Scope <String[]>] [-AppDiskDescription <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AppLibAppDisk [-AppDiskName] <String> -SourceAppDiskUid <Guid> -PreparationMachine <String> [-AppDiskDescription <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

New-AppLibAppDisk [-AppDiskName] <String> -SourceAppDiskName <String> -PreparationMachine <String> [-AppDiskDescription <String>] [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Lets you create a new AppDisk.


## Related Commands

* [Get-AppLibTask](./Get-AppLibTask/)
* [Get-AppLibAppDisk](./Get-AppLibAppDisk/)
* [Import-AppLibAppDisk](./Import-AppLibAppDisk/)
* [Test-AppLibAppDiskNameAvailable](./Test-AppLibAppDiskNameAvailable/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk to be created.  This must be a name that is not being used by an existing AppDisk, and it must not contain any of the following characters \\/;:#.\*?=&lt;&gt;|\[\]()""' | true | false |  |
| PreparationMachine | The SID of the machine to use as the preparation machine for this operation. The machine must be within a valid Machine Catalog. | true | false |  |
| HostingUnitName | The name of the hosting unit used for the AppDisk. | true | false |  |
| DiskSizeMB | How large the AppDisk should be, in megabytes. | true | false |  |
| HostingUnitUid | The identifier for the hosting unit used for the AppDisk. | true | false |  |
| SourceAppDiskUid | Identifies an AppDisk to be used as a basis for this one. | true | false |  |
| SourceAppDiskName | Identifies an AppDisk to be used as a basis for this one. | true | false |  |
| AppDiskDescription | The description of the AppDisk. | false | false |  |
| RunAsynchronously | Indicates whether or not the command returns before it is complete. If specified, the command returns an identifier for the task that was created. This task can be monitored using the Get-AppLibTask command. | false | false | false |
| PurgeJobOnSuccess | Indicates that the task history is removed from the database when the task has finished. This can only be specified for tasks that are not run asynchronously. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |
| Scope | The administration scopes to be applied to the new AppDisk. | false | false |  |

## Input Type

### 

## Return Values

### System.Guid
When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier
### System.Management.Automation.Pscustomobject
System.Management.Automation.PSCustomObject This object provides details of the task that was run and contains the following information:<br>TaskId &lt;Guid&gt; The identifier for the task that was performed. Active &lt;Boolean&gt; Indicates whether the task is still processing or is complete. Host &lt;string&gt; The name of the host on which the task is running or was run. DateStarted &lt;DateTime&gt; The date and time that the task was initiated. LastUpdateTime &lt;DateTime&gt; The date and time of the last task status update DateFinished &lt;DateTime&gt; The date and time that the task finished execution Metadata &lt;Metadata\[\]&gt; Associated key-value data TaskState &lt;string&gt; Where in its lifecycle the task is CurrentOperation &lt;string&gt; Operation specific phase of the overall "Running" task state. TerminatingError &lt; Citrix.Fma.Sdk.ServiceCore.CommonCmdlets.TaskterminatingError&gt; Diagnostic information in the case of a complete task failure ActiveElapsedTime &lt;int&gt; How many seconds of active execution the task has taken Type &lt;string&gt; The type of task. For this cmdlet's tasks, this is always NewAppDisk. AppDiskName &lt;string&gt; The name of the AppDisk that the task was for. AppDiskUid &lt;string&gt; The identifier of the AppDisk that the task was for. Scopes &lt;Citrix.Fma.Sdk.ServiceCoreScopeReference\[\]&gt; The delegated administration scopes to which the AppDisk will belong. TaskStateInformation &lt;string&gt; Additional information about the current task state. TaskProgress &lt;double&gt; The progress of the task 0-100%. DiskSizeMB &lt;int&gt; The size of the AppDisk DiskLocalUid &lt;Guid&gt; The identifier of the AppDisk lineage. DiskLocalVersion &lt;Guid&gt; The identifier of the AppDisk within its lineage. RemoteTaskId &lt;Guid&gt; The identifier of the associated disk management task on the Machine Creation Service HostingUnitName &lt;string&gt; The name of the associated hosting unit HostingUnitUid &lt;Guid&gt; The indentifier of the associated hosting unit VirtualDiskId &lt;Guid&gt; The identifier of the AppDisk stack ReservedMachineSid  &lt;string&gt; Security identifier of the VM being used to perform the operation
## Notes
Only one long-running task for each AppDisk can be processed at a time.<br>    In case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation. Communication with the database failed<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidParameterCombination<br>    Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    ScopeNotFound<br>    One or more of the scopes nominated for the new AppDisk do not exist.<br>    ExceptionThrown<br>    The cmdlet is associated with a task of type NewAppDisk, and while active will move through the following operations (CurrentOperation field)<br>    ValidatingInputs<br>    ConsolidatingMasterImage<br>    PreparingMasterImage<br>    ReplicatingMasterImage<br>    CommittingScheme
## Examples

### Example 1
```
C:\PS> New-AppLibAppDisk -AppDiskName MyAppDisk -HostingUnitName XenHu -DiskSizeMB 16384 -PreparationMachine S-1-5-21-2316621082-1546847349-2782505528-1165

          TaskId                              : 90e93b9d-a225-4701-ad50-fa1546af35ac

          AppDiskName                         : MyAppDisk

          AppDiskUid                          : d9ba6487-05f8-48ad-a178-1794605e2b8e

          Active                              : False

          DiskSizeMB                          : 16384

          DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297

          DiskLocalVersion                    : 25118c6e-a737-4fb9-b4b3-121910a73160

          DateStarted                         : 17/11/2015 08:22:22

          LastUpdateTime                      : 17/11/2015 09:10:18

          DateFinished                        : 17/11/2015 09:10:18

          Type                                : NewAppDisk

          Metadata                            : {}

          TaskState                           : Finished

          TaskStateInformation                :

          TaskProgress                        : 100

          TerminatingError                    :

          RemoteTaskId                        : d2127904-a149-4dce-ae82-f9671a53f6fd

          HostingUnitName                     : XenHU

          HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

          Host                                : MyHost

          VirtualDiskId                       : 7ce3c9a5-2888-45ba-8629-398f9e4eba7d

          CurrentOperation                    :

          ActiveElapsedTime                   : 2786

          ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165
```
#### Description
Creates a new 16Gb AppDisk with the name "MyAppDisk" using the hosting unit "XenHu", using the preparation machine "S-1-5-21-2316621082-1546847349-2782505528-1165".
### Example 2
```
C:\PS> New-AppLibAppDisk -AppDiskName MyUpdatedAppDisk -AppDiskDescription "Includes new applications" -SourceAppDisk MyAppDisk -PreparationMachine S-1-5-21-2316621082-1546847349-2782505528-1165 -RunAsynchronously

          Guid

          ----

          6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
```
#### Description
Asynchronously creates a new AppDisk "MyUpdatedAppDisk" from "MyAppDisk", using the preparation machine "S-1-5-21-2316621082-1546847349-2782505528-1165". To get the task details, use Get-AppLibTask -TaskID &lt;task id&gt;&lt;br&gt;i.e.&lt;br&gt;C:\\PS&gt;Get-AppLibTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b&lt;br&gt;TaskId                              : 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b AppDiskName                         : MyUpdatedAppDisk AppDiskUid                          : 3b9c6b62-be1e-467b-9cb4-025ad9cba916 Active                              : False DiskSizeMB                          : DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297 DiskLocalVersion                    : a23f8bae-dedf-433f-8908-025144ff4f81 DateStarted                         : 23/11/2015 12:09:53 LastUpdateTime                      : 23/11/2015 13:01:26 DateFinished                        : 23/11/2015 13:01:26 Type                                : NewAppDisk Metadata                            : {} TaskState                           : Finished TaskStateInformation                : TaskProgress                        : 100 TerminatingError                    : RemoteTaskId                        : 0ab9e8ed-1ded-4831-80c3-9cf84e752528 HostingUnitName                     : XenHU HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501 Host                                : MyHost VirtualDiskId                       : 4c245ff7-5cdd-4aac-a854-1e101e23d1f6 CurrentOperation                    : ActiveElapsedTime                   : 3079 ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165
