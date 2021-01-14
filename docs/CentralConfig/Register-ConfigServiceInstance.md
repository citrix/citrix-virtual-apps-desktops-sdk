
# Register-Configserviceinstance
Allows the registration of a service instance.
## Syntax
```
Register-ConfigServiceInstance -ServiceGroupUid <Guid> -ServiceGroupName <String> -ServiceType <String> -Address <String> -Binding <String> -Version <Int32> -ServiceAccount <String> -InterfaceType <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Register-ConfigServiceInstance -ServiceGroupUid <Guid> -ServiceGroupName <String> -ServiceType <String> -Address <String> -Binding <String> -Version <Int32> -ServiceAccountSid <String> -InterfaceType <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Register-ConfigServiceInstance -ServiceInstance <ServiceInstance[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this cmdlet to register service instance items in the Configuration Service. Service instances can be registered either by retrieving the data directly from other services or by manually entering the details into this command.

If the service group specified by the service instance already exists, the service is added to the service group, otherwise a new service group is created to hold the service instance.


## Related Commands

* [Unregister-ConfigRegisteredServiceInstance](./Unregister-ConfigRegisteredServiceInstance/)
* [Add-ConfigRegisteredServiceInstanceMetadata](./Add-ConfigRegisteredServiceInstanceMetadata/)
* [Set-ConfigRegisteredServiceInstanceMetadata](./Set-ConfigRegisteredServiceInstanceMetadata/)
* [Remove-ConfigRegisteredServiceInstanceMetadata](./Remove-ConfigRegisteredServiceInstanceMetadata/)
* [Add-ConfigServiceGroupMetadata](./Add-ConfigServiceGroupMetadata/)
* [Set-ConfigServiceGroupMetadata](./Set-ConfigServiceGroupMetadata/)
* [Remove-ConfigServiceGroupMetadata](./Remove-ConfigServiceGroupMetadata/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceGroupUid | The Service Group Unique Identifier | true | true (ByPropertyName) |  |
| ServiceGroupName | The name of the service group | true | true (ByPropertyName) |  |
| ServiceType | The type of the service group | true | true (ByPropertyName) |  |
| Address | The address that is used to access the service instance. | true | true (ByPropertyName) |  |
| Binding | The binding type that must be used to access the service instance. | true | true (ByPropertyName) |  |
| Version | The version of the service instance. | true | true (ByPropertyName) |  |
| ServiceAccount | The AD computer account name (domain qualified) for the computer on which the service instance is hosted. | true | true (ByPropertyName) |  |
| InterfaceType | The type of interface that the service provides (i.e. SDK, InterService, Peer). | true | true (ByPropertyName) |  |
| ServiceAccountSid | The AD computer account Sid for the computer on which the service instance is hosted. | true | true (ByPropertyName) |  |
| ServiceInstance | The service instances to register. | true | true (ByValue) |  |
| LoggingId | Specifies the logging id of the high-level operation that this cmdlet is part of. | false | true (ByPropertyName) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can be provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Configuration.Sdk.Serviceinstance<br>   An Object With The Following Parameters Can Be Used To Register A Service Instance.<br>     Address,<br>     Servicegroupuid,<br>     Servicegroupname,<br>     Servicetype,<br>     Binding,<br>     Version,<br>     Interfacetype.

## Return Values

### Citrix.Configuration.Sdk.Serviceinstance
This represents a service instance and has the following parameters;<br>    ServiceGroupUid &lt;Guid&gt;<br>        The unique identifier for the service group to which the service instance belongs.<br>    ServiceGroupName &lt;string&gt;<br>        The name of the service group to which the service instance belongs.<br>    ServiceInstanceUid &lt;Guid&gt;<br>        The unique identifier for the service instance.<br>    ServiceType &lt;string&gt;<br>        The type of the service group.<br>    Address &lt;string&gt;<br>        The contact address for the service instance.<br>    Binding &lt;string&gt;<br>        The binding to use for connections to the service instance.<br>    Version &lt;int&gt;<br>        The version of the service instance.<br>    ServiceAccount &lt;string&gt;<br>        The AD computer account for the computer that is providing the service instance.<br>    ServiceAccountSid &lt;string&gt;<br>        The AD computer account SID for the computer that is providing the service instance.<br>    InterfaceType &lt;string&gt;<br>        The interface type for the service instance.<br>    Metadata &lt;Citrix.Configuration.Sdk.Metadata\[\]&gt;<br>        The metadata for the service instance.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes ----------- ActiveDirectoryAccountResolutionFailed The account name provided could not be found in Active Directory. ServiceGroupWithSameUidExistsForDifferentServiceGroupNameOrSameUidExistsForDifferentServiceGroupNameOrServiceType The service group name or service type do not match the service group found with the specified uid. TypeAlreadyExists A different service group with the same type is registered already in the Configuration Service. DatabaseError An error occurred in the service while attempting a database operation. DatabaseNotConfigured The operation could not be completed because the database for the service is not configured. DataStoreException An error occurred in the service while attempting a database operation - communication with the database failed for various reasons. CommunicationError An error occurred while communicating with the service. ExceptionThrown An unexpected error occurred.  For more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-ConfigServiceInstance | Register-ConfigServiceInstance
```
#### Description
Gets the service instances for the Configuration Service and registers them.
