
# Invoke-Applibappdiskdnaimport
Imports a given AppDisk into AppDNA
## Syntax
```
Invoke-AppLibAppDiskDnaImport -AppDiskName <String> -ReservedMachine <String> [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Invoke-AppLibAppDiskDnaImport -AppDiskUid <Guid> -ReservedMachine <String> [-RunAsynchronously] [-PurgeJobOnSuccess] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Will extract metadata from a provided AppDisk, import it into AppDNA and start an analysis of the imported metadata.


## Related Commands

* [Enable-AppLibAppDNAConnection](./Enable-AppLibAppDNAConnection/)
* [Get-AppLibTask](./Get-AppLibTask/)
* [Stop-AppLibTask](./Stop-AppLibTask/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AppDiskName | The name of the AppDisk. | true | false |  |
| AppDiskUid | The unique identifier of the AppDisk. | true | false |  |
| ReservedMachine | The SID of the machine to use for this operation. The machine must be within a valid Machine Catalog. | true | false |  |
| RunAsynchronously | Return immediately with the identifier for the running task. | false | false |  |
| PurgeJobOnSuccess | Purge the job from the list of tasks if successful. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### System.Guid
When the RunAsynchronously identifier is specified, this GUID is returned and provides the task identifier.
### System.Management.Automation.Pscustomobject
This object provides details of the task that was run and contains the following information:<br>TaskId &lt;Guid&gt; The identifier for the task that was performed. Active &lt;Boolean&gt; Indicates whether the task is still processing or is complete. Host &lt;string&gt; The name of the host on which the task is running or was run. DateStarted &lt;DateTime&gt; The date and time that the task was initiated. LastUpdateTime &lt;DateTime&gt; The date and time of the last task status update DateFinished &lt;DateTime&gt; The date and time that the task finished execution Metadata &lt;Metadata\[\]&gt; Associated key-value data TaskState &lt;string&gt; Where in its lifecycle the task is CurrentOperation &lt;string&gt; Operation specific phase of the overall "Running" task state. TerminatingError &lt; Citrix.Fma.Sdk.ServiceCore.CommonCmdlets.TaskterminatingError&gt; Diagnostic information in the case of a complete task failure ActiveElapsedTime &lt;int&gt; How many seconds of active execution the task has taken Type &lt;string&gt; The type of task. For this cmdlet's tasks, this is always ImportAppDiskDNA. TaskStateInformation &lt;string&gt; Additional information about the current task state. TaskProgress &lt;double&gt; The progress of the task 0-100%. AppDiskName &lt;string&gt; The name of the AppDisk that the task was for. AppDiskUid &lt;string&gt; The identifier of the AppDisk that the task was for. DiskLocalUid &lt;Guid&gt; The identifier of the AppDisk lineage. DiskLocalVersion &lt;Guid&gt; The identifier of the AppDisk within its lineage. HostingUnitName &lt;string&gt; The name of the associated hosting unit HostingUnitUid &lt;Guid&gt; The indentifier of the associated hosting unit VirtualDiskId &lt;Guid&gt; The identifier of the AppDisk stack ReservedMachineSid  &lt;string&gt; Security identifier of the VM being used to perform the operation TemporaryVirtualDiskId &lt;Guid&gt; The identifier of the AppDisk stack used for intermediate stages of the analysis AppDiskMetadataFileNamesList &lt;string\[\]&gt; Metadata files associated with the analysis LocalAppDiskMetadataDirectory &lt;string&gt; Directory containing the metadata files
## Notes
Only one long-running task for each AppDisk can be processed at a time.<br>    In case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    JobCreationFailed<br>    The requested task could not be started.<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation. Communication with the database failed<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidParameterCombination<br>    Both PurgeJobOnSuccess and RunAsynchronously were specified. When running asynchronously, the cmdlet terminates before the job does, so it cannot clean up the completed job.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error.<br>    ExceptionThrown<br>    An unexpected error occurred. To locate more details, see the Windows event logs on the controller being used, or examine the XenDesktop logs.<br>    AppDiskNotFound<br>    The specified AppDisk was not found.<br>    AppDiskInInvalidState<br>    The disk was not in the "Ready" state.<br>    AppDNAAnalysisAlreadyPerformed<br>    There is no new analysis to perform here<br>    BrokerMachineNotReserved<br>    The indicated machine could not be reserved for the operation<br>    This cmdlet will return an error in the event that the AppDNA integration has not been configured. See Enable-AppLibAppDNAConnection for details.
## Examples

### Example 1
```
C:\PS> Invoke-AppLibAppDiskDnaImport -AppDiskName MyAppDisk

          TaskId                              : 90e93b9d-a225-4701-ad50-fa1546af35ac

          AppDiskName                         : MyAppDisk

          AppDiskUid                          : d9ba6487-05f8-48ad-a178-1794605e2b8e

          Active                              : False

          DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297

          DiskLocalVersion                    : 25118c6e-a737-4fb9-b4b3-121910a73160

          DateStarted                         : 17/11/2015 08:22:22

          LastUpdateTime                      : 17/11/2015 09:10:18

          DateFinished                        : 17/11/2015 09:10:18

          Type                                : ImportAppDiskDNA

          Metadata                            : {}

          TaskState                           : Finished

          TaskStateInformation                :

          TaskProgress                        : 100

          TerminatingError                    :

          TemporaryVirtualDiskId              : d2127904-a149-4dce-ae82-f9671a53f6fd

          HostingUnitName                     : XenHU

          HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501

          Host                                : MyHost

          VirtualDiskId                       : 7ce3c9a5-2888-45ba-8629-398f9e4eba7d

          CurrentOperation                    :

          ActiveElapsedTime                   : 2786

          ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165

          AppDiskMetadataFileNamesList        : { F:\AppDiskMetadata.xml }

          LocalAppDiskMetadataDirectory       : C:\Windows\Temp\90e93b9d-a225-4701-ad50-fa1546af35ac
```
#### Description
Initiate the import and analysis of the AppDisk with the name "MyAppDisk".
### Example 2
```
C:\PS> New-AppLibAppDisk -AppDiskUid M3b9c6b62-be1e-467b-9cb4-025ad9cba916 -RunAsynchronously

          Guid

          ----

          6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
```
#### Description
Asynchronously initiate the import and analysis of the AppDisk with the name "MyAppDisk".. To get the task details, use Get-AppLibTask -TaskID &lt;task id&gt;&lt;br&gt;i.e.&lt;br&gt;C:\\PS&gt;Get-AppLibTask -TaskID 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b&lt;br&gt;TaskId                              : 6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b AppDiskName                         : MyUpdatedAppDisk AppDiskUid                          : 3b9c6b62-be1e-467b-9cb4-025ad9cba916 Active                              : False DiskLocalUid                        : 7b4c01c4-72fa-4c80-913d-c6df785f4297 DiskLocalVersion                    : 25118c6e-a737-4fb9-b4b3-121910a73160 DateStarted                         : 17/11/2015 08:22:22 LastUpdateTime                      : 17/11/2015 09:10:18 DateFinished                        : 17/11/2015 09:10:18 Type                                : ImportAppDiskDNA Metadata                            : {} TaskState                           : Finished TaskStateInformation                : TaskProgress                        : 100 TerminatingError                    : TemporaryVirtualDiskId              : d2127904-a149-4dce-ae82-f9671a53f6fd HostingUnitName                     : XenHU HostingUnitUid                      : 01a4a008-8ce8-4165-ba9c-cdf15a6b0501 Host                                : MyHost VirtualDiskId                       : 7ce3c9a5-2888-45ba-8629-398f9e4eba7d CurrentOperation                    : ActiveElapsedTime                   : 2786 ReservedMachineSid                  : S-1-5-21-2316621082-1546847349-2782505528-1165 AppDiskMetadataFileNamesList        : { F:\\AppDiskMetadata.xml } LocalAppDiskMetadataDirectory       : C:\\Windows\\Temp\\6dd85fec-96cf-46b1-9cd4-d8ba7d06e85b
