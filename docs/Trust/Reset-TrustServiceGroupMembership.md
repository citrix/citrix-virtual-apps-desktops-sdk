
# Reset-Trustservicegroupmembership
Reloads the access permissions and configuration service locations for the Trust Service.
## Syntax
```
Reset-TrustServiceGroupMembership [-ConfigServiceInstance] <ServiceInstance[]> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Enables you to reload Trust Service access permissions and configuration service locations.  The Reset-TrustServiceGroupMembership command must be run on at least one instance of the service type (Trust) after installation and registration with the configuration service.  Without this operation, the Trust services will be unable to communicate with other services in the XenDesktop deployment.  When the command is run, the services are updated when additional services are added to the deployment, provided that the configuration service is not stopped.  The Reset-TrustServiceGroupMembership command can be run again to refresh this information if automatic updates do not occur when new services are added to the deployment.  If more than one configuration service instance is passed to the command, the first instance that meets the expected service type requirements is used.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ConfigServiceInstance | Specifies the configuration service instance object that represents the service instance for the type 'InterService' that references a configuration service for the deployment. | true | true (ByValue) |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### Citrix.Trust.Sdk.Serviceinstance\[\]<br>Service Instances Containing A Serviceinstance Object That Refers To The Central Configuration Service Inter-Service Interface Can Be Piped To The Reset-Trustservicegroupmembership Command.

## Return Values

### 

## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    NoSuitableServiceInstance<br>        None of the supplied service instance objects were suitable for resetting service group membership.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    ConfigurationLoggingError<br>        The operation could not be performed because of a configuration logging error.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-ConfigRegisteredServiceInstance -ServiceType Config | Reset-TrustServiceGroupMembership
```
#### Description
Reset the service group membership for a service in a deployment where the configuration service is configured and running on the same machine as the service.
### Example 2
```
c:\PS>Get-ConfigRegisterdServiceInstance -ServiceType Config -AdminAddress OtherServer.example.com | Reset-TrustServiceGroupmembership
```
#### Description
Reset the service group membership for a service in a deployment where the configuration service that is configured and running on a machine named 'OtherServer.example.com'.
