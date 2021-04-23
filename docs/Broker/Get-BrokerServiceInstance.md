
# Get-Brokerserviceinstance
Gets the service instance entries for the Broker Service.
## Syntax
```
Get-BrokerServiceInstance [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
Returns service interfaces published by instances of the Broker Service. Each instance of a service publishes multiple interfaces with distinct interface types, and each of these interfaces is represented as a ServiceInstance object. Service instances can be used to register the service with a central configuration service so that other services can use the functionality.

You do not need to configure a database connection to use this command.


## Related Commands

* [Get-BrokerServiceStatus](./Get-BrokerServiceStatus/)
* [Reset-BrokerServiceGroupMembership](./Reset-BrokerServiceGroupMembership/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Broker.Sdk.Serviceinstance
The Get-BrokerServiceInstance command returns an object containing the following properties.<br>ServiceGroupUid &lt;Guid&gt;<br>    Specifies the unique identifier for the service group of which the service is a member.<br>ServiceGroupName &lt;String&gt;<br>    Specifies the name of the service group of which the service is a member.<br>ServiceInstanceUID &lt;Guid&gt;<br>    Specifies the unique identifier for registered service instances, which are service instances held by and obtained from a central configuration service.  Unregistered service instances do not have unique identifiers.<br>ServiceType &lt;String&gt;<br>    Specifies the service instance type.  For this service, the service instance type is always Broker.<br>Address<br>    Specifies the address of the service instance.  The address can be used to access the service and, when registered in the central configuration service, can be used by other services to access the service.<br>Binding<br>    Specifies the binding type that must be used to communicate with the service instance.  In this release of XenDesktop, the binding type is always 'wcf\_HTTP\_kerb'. This indicates that the service provides a Windows Communication Foundation endpoint that uses HTTP binding with integrated authentication.<br>Version<br>    Specifies the version of the service instance.  The version number is used to ensure that the correct versions of the services are used for communications.<br>ServiceAccount &lt;String&gt;<br>    Specifies the Active Directory account name for the machine on which the service instance is running.  The account name is used to provide information about the permissions required for interservice communications.<br>ServiceAccountSid &lt;String&gt;<br>    Specifies the Active Directory account security identifier for the machine on which the service instance is running.<br>InterfaceType &lt;String&gt;<br>    Specifies the interface type.  Each service can provide multiple service instances, each for a different purpose, and the interface defines the purpose.  Available interfaces are:<br>        SDK - for PowerShell operations<br>        InterService - for operations between different services<br>        Peer - for communications between services of the same type<br>Metadata &lt;Citrix.Broker.Sdk.Metadata\[\]&gt;<br>     The collection of metadata associated with registered service instances, which are service instances held by and obtained from a central configuration service.  Metadata is not stored for unregistered service instances.
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-BrokerServiceInstance
```
#### Description
Get all instances of the Broker Service running on the specified machine.  For remote services, use the AdminAddress parameter to define the service for which the interfaces are required. If the AdminAddress parameter has not been specified for the runspace, service instances running on the local machine are returned.
