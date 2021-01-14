
# Test-Configserviceinstanceavailability
Tests whether the supplied service instances are responding to requests.
## Syntax
```
Test-ConfigServiceInstanceAvailability [-ServiceInstance] <ServiceInstance[]> [-MaxDelaySeconds <Int32>] [-ForceWaitForOneOfEachType] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description



## Related Commands

* [Register-ConfigServiceInstance](./Register-ConfigServiceInstance/)
* [Unregister-ConfigRegisteredServiceInstance](./Unregister-ConfigRegisteredServiceInstance/)
* [Get-ConfigRegisteredServiceInstance](./Get-ConfigRegisteredServiceInstance/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ServiceInstance | The service instances to test. | true | true (ByValue) |  |
| MaxDelaySeconds | The timeout period to wait before concluding that services are unresponsive. | false | false | Infinite |
| ForceWaitForOneOfEachType | If at least one of each type of service responds, finish immediately. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the host name or IP address of the controller to which the PowerShell snap-in connects. | false | false | 'LocalHost'.  Once a value is specified by any command, this value becomes the new default. |

## Input Type

### 

## Return Values

### System.Management.Automation.Psobject
This represents a service instance and has the following parameters;<br>    ServiceGroupUid &lt;Guid&gt;<br>        The unique identifer for the service group to which the service instance belongs.<br>    ServiceGroupName &lt;string&gt;<br>        The name of the service group that the service instance is part of.<br>    ServiceInstanceUid &lt;Guid&gt;<br>        The unique identifier for the service instance.<br>    ServiceType &lt;string&gt;<br>        The type of the service group.<br>    Address &lt;string&gt;<br>        The contact address for the service instance.<br>    Binding &lt;string&gt;<br>        The binding to use for connections to the service instance.<br>    Version &lt;int&gt;<br>        The version of the service instance.<br>    ServiceAccount &lt;string&gt;<br>        The AD computer account for the computer that is providing the service instance.<br>    ServiceAccountSid &lt;string&gt;<br>        The AD computer account SID for the computer that is providing the service instance.<br>    InterfaceType &lt;string&gt;<br>        The interface type for the service instance.<br>    Metadata &lt;Citrix.Configuration.Sdk.Metadata\[\]&gt;<br>        The metadata for the service instance.<br>    Status &lt;Citrix.Configuration.Sdk.Commands.Availability&gt;<br>        An enumeration value indicating whether the service is Responding, NotResponding, Unknown, or BadBindingType.<br>    ResponseTime &lt;System.TineSpan&gt;<br>        The interval elapsed between hailing the service and getting a definite response
## Notes
The Availability Status Codes are o Responding: Got a positive response o NotResponding: Got a response, but it was negative or the connection was refused o Unknown: Did not respond in time / timed-out o BadBindingType: Binding parameter in ServiceInstance is not wcf\_HTTP\_kerb
## Examples

### Example 1
```
C:\>Get-ConfigRegisteredServiceInstance | Test-ConfigServiceInstanceAvailability -ForceWaitForOneOfEachType
```
#### Description
Test all the service instances that are registered in the Configuration Service, returning when one of each type is responding.
### Example 2
```
C:\>Test-ConfigServiceInstanceAvailability -ServiceInstance $services -MaxDelaySeconds 5
```
#### Description
Test each of the given services, allowing a 5 second time-out.
