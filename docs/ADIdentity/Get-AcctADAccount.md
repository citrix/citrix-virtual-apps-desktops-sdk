
# Get-Acctadaccount
Gets the AD accounts stored in the AD Identity Service.
## Syntax
```
Get-AcctADAccount [-IdentityPoolName <String>] [-ADAccountSid <String>] [-Domain <String>] [-State <ADIdentityState>] [-Lock <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Get-AcctADAccount [-IdentityPoolUid <Guid>] [-ADAccountSid <String>] [-Domain <String>] [-State <ADIdentityState>] [-Lock <Boolean>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Provides the ability to locate the AD accounts stored within the AD Identity Service and view the state of the accounts.


## Related Commands

* [New-AcctADAccount](./New-AcctADAccount/)
* [Add-AcctADAccount](./Add-AcctADAccount/)
* [Remove-AcctADAccount](./Remove-AcctADAccount/)
* [Unlock-AcctADAccount](./Unlock-AcctADAccount/)
* [Update-AcctADAccount](./Update-AcctADAccount/)
* [Repair-AcctADAccount](./Repair-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ADAccountSid | The AD Account SID of the account. | false | false |  |
| Domain | The domain of the account (this is in dns format). | false | false |  |
| State | The current state of the identity stored in the AD Identity Service for the AD account. | false | false |  |
| Lock | Indicates if the account is locked in the AD Identity Service. | false | false |  |
| ReturnTotalRecordCount | See about\_Acct\_Filtering for details. | false | false | false |
| MaxRecordCount | See about\_Acct\_Filtering for details. | false | false | 250 |
| Skip | See about\_Acct\_Filtering for details. | false | false | 0 |
| SortBy | See about\_Acct\_Filtering for details. | false | false |  |
| Filter | See about\_Acct\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |
| IdentityPoolName | The name of the identity pool to which the account is registered. | false | true (ByPropertyName) |  |
| IdentityPoolUid | The unique identifier for the identity pool that the account is registered to. | false | false |  |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Identityinpool
The Get-AcctADAccount returns an object that contains the following parameters<br>        ADAccountSid &lt;string&gt;<br>            The AD account SID for the retrieved account.<br>        ADAccountName &lt;string&gt;<br>          The AD account name for the retrieved account.<br>          Domain &lt;string&gt;<br>            The domain for the imported account.<br>        State &lt;Citrix.XDInterServiceTypes.ADIdentityState&gt;<br>            The state for the account. This can be;<br>                Available<br>                    The account is not used.<br>                InUse<br>                    The account is in use.<br>                Error<br>                    The account is in error (i.e. the account is locked or disabled in AD).<br>                Tainted<br>                     The account is no longer used, but the password is no longer known.<br>        Lock &lt;Boolean&gt;<br>            The account is locked (in the database not in AD).<br>        IdentityPoolName &lt;System.String&gt;<br>            The name of the containing identity pool.<br>        IdentityPoolUid &lt;System.Guid&gt;<br>            The GUID identifying the containing identity pool.
## Notes
In the case of failure the following errors can result.<br>    Error Codes<br>    -----------<br>    PartialData<br>    Only a subset of the available data was returned.<br>    CouldNotQueryDatabase<br>    The query required to get the database was not defined.<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\>Get-AcctADAccount
```
#### Description
Return all the AD accounts that are registered in the AD Identity Service.
### Example 2
```
C:\>Get-AcctADAccount -IdentityPoolName MyPool -Lock $false
```
#### Description
Return all the AD accounts that are registered in the AD Identity Service in the identity pool called "MyPool" that are also locked.
### Example 3
```
C:\>Get-AcctADAccount -Filter {IdentityPoolName -Like "p\*" -or IdentityPoolName -eq "MyPool"}
```
#### Description
Return all the AD accounts that are registered in the AD Identity Service in the identity pool called "MyPool" or in an identity pool that has a name that starts with a 'p'.  For full details of the advanced filtering aspects of this command see about\_Acct\_Filtering.
