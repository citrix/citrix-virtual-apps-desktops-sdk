
# Get-Acctidentitypool
Gets existing identity pools.
## Syntax
```
Get-AcctIdentityPool [[-IdentityPoolName] <String>] [-IdentityPoolUid <Guid>] [-Lock <Boolean>] [-ScopeId <Guid>] [-ScopeName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to locate existing identity pools.


## Related Commands

* [New-AcctIdentityPool](./New-AcctIdentityPool/)
* [Remove-AcctIdentityPool](./Remove-AcctIdentityPool/)
* [Rename-AcctIdentityPool](./Rename-AcctIdentityPool/)
* [Set-AcctIdentityPool](./Set-AcctIdentityPool/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| IdentityPoolName | The name of the identity pool. | false | false |  |
| IdentityPoolUid | The unique identifier for the identity pool. | false | false |  |
| Lock | Whether the identity pool is locked or not. | false | false |  |
| ScopeId | Gets only results with a scope matching the specified scope identifier. | false | false |  |
| ScopeName | Gets only results with a scope matching the specified scope name. | false | false |  |
| ReturnTotalRecordCount | See about\_Acct\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Acct\_Filtering for details. | false | false | 250 |
| Skip | See about\_Acct\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Acct\_Filtering for details. | false | false |  |
| Filter | See about\_Acct\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value will become the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Identitypool
This object provides details of the identity pool and contains the following information:<br>IdentityPoolName &lt;string&gt;<br>    The name of the identity pool.<br>IdentityPoolUid &lt;Guid&gt;<br>    The unique identifier for the identity pool.<br>NamingScheme &lt;string&gt;<br>    The naming scheme for the identity pool.<br>NamingSchemeType &lt;Citrix.XDInterServiceTypes.ADIdentityNamingScheme&gt;<br>    The naming scheme type for the identity pool. This can be one of the following:<br>        Numeric - naming scheme uses numeric indexes<br>        Alphabetic - naming scheme uses alphabetic indexes<br>StartCount &lt;int&gt;<br>    The next index to be used when creating an identity from the identity pool.<br>OU &lt;string&gt;<br>    The Active Directory distinguished name for the OU in which accounts created from this identity pool will be created.<br>Domain &lt;string&gt;<br>    The Active Directory domain that accounts in the pool belong to.<br>Lock &lt;Boolean&gt;<br>    Indicates if the identity pool is locked.
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Get-AcctIdentityPool

IdentityPoolName : MyPool

IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915

NamingScheme     : Acc####

NamingSchemeType : Numeric

StartCount       : 1

OU               :

Domain           : mydomain.com

Lock             : True

IdentityPoolName : MyPool2

IdentityPoolUid  : 03743136-e43b-4a87-af74-ab71686b3c16

NamingScheme     : Test####

NamingSchemeType : Alphabetic

StartCount       : 1

OU               :

Domain           : mydomain.com

Lock             : False
```
#### Description
Gets all the identity pools.
### Example 2
```
C:\PS>Get-AcctIdentityPool -IdentityPoolName M\*

IdentityPoolName : MyPool

IdentityPoolUid  : 22072d9e-6a8f-494b-a5bc-2ef18ca4b915

NamingScheme     : Acc####

NamingSchemeType : Numeric

StartCount       : 1

OU               :

Domain           : mydomain.com

Lock             : True
```
#### Description
Gets all the identity pools beginning with the character 'M'.
