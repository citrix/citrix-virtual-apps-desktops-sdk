
# Test-Acctidentitypoolnameavailable
Checks to ensure that the proposed name for an identity pool is unused.
## Syntax
```
Test-AcctIdentityPoolNameAvailable [-IdentityPoolName] <String[]> [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Checks to ensure that the proposed name for an identity pool is unused. This check is done without regard for scoping of existing identity pools, so the names of inaccessible pools are also checked.


## Related Commands

* [New-AcctIdentityPool](./New-AcctIdentityPool/)
* [Rename-AcctIdentityPool](./Rename-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name or names of the identity pool(s) to be tested. | true | true (ByValue, ByPropertyName) |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Object\[\]
An array of PSObjects that pair the name and availability of the name
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
Test-AcctIdentityPoolNameAvailable -IdentityPoolName $NewPoolName
```
#### Description
This tests whether the value of \$NewPoolName is unique or not, and can be used to create a new provisioning scheme or rename an existing one without failing. True is returned if the name is good.
