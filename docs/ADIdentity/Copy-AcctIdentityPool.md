
# Copy-Acctidentitypool
Copies an Identity Pool and its associated Identities to a new IdentityPool
## Syntax
```
Copy-AcctIdentityPool [-IdentityPoolName] <String> [-NewIdentityPoolName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Copy-AcctIdentityPool -IdentityPoolUid <Guid> [-NewIdentityPoolName] <String> [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to copy an IdentityPool.

The new IdentityPool will contain all the accounts that were in the original pool and will have the same domain and OU set. The naming scheme will be unset and the StartCount will be set to 1.


## Related Commands

* [New-AcctIdentityPool](./New-AcctIdentityPool/)
* [Get-AcctIdentityPool](./Get-AcctIdentityPool/)
* [Remove-AcctIdentityPool](./Remove-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool that is to be copied. | true | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool that is to be copied. | true | false |  |
| NewIdentityPoolName | The name for the new IdentityPool. | true | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Identitypool
This object provides details of the new identity pool and contains the following information:<br>          IdentityPoolName &lt;string&gt;<br>          The name of the identity pool.<br>          IdentityPoolUid &lt;Guid&gt;<br>          The unique identifier for the identity pool.<br>          NamingScheme &lt;string&gt;<br>          The naming scheme for the identity pool.<br>          NamingSchemeType &lt;Citrix.XDInterServiceTypes.ADIdentityNamingScheme&gt;<br>          The naming scheme type for the identity pool. This can be one of the following:<br>          Numeric - naming scheme uses numeric indexes<br>          Alphabetic - naming scheme uses alphabetic indexes<br>          StartCount &lt;int&gt;<br>          The next index to be used when creating an identity from the identity pool.<br>          OU &lt;string&gt;<br>          The Active Directory distinguished name for the OU in which accounts created from this identity pool will be created.<br>          Domain &lt;string&gt;<br>          The Active Directory domain that accounts in the pool belong to.<br>          Lock &lt;Boolean&gt;<br>          Indicates whether the identity pool is locked.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    IdentityPoolDuplicateObjectExists<br>    An identity pool with the same name exists already.<br>    IdentityPoolObjectNotFound<br>    The identity pool to be modified could not be located.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with the database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```

```
#### Description

