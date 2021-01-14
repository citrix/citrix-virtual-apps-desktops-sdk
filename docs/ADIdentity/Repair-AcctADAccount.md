
# Repair-Acctadaccount
Resets the Active Directory machine password for the given accounts.
## Syntax
```
Repair-AcctADAccount -ADAccountName <String[]> [-Password <String>] [-SecurePassword <SecureString>] [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]

Repair-AcctADAccount -ADAccountSid <String[]> [-Password <String>] [-SecurePassword <SecureString>] [-ADUserName <String>] [-ADPassword <SecureString>] [-Force] [-LoggingId <Guid>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
This provides the ability to synchronize the account password stored in Active Directory with the password stored in the AD Identity Service.  If successful, this results in the AD Identity Service account state being reset to 'available' so it can be consumed by other Machine Creation Services.

If the current account password is not supplied using the Password or SecurePassword Parameters, this requires the user who initiated the runspace to have the required permissions in Active Directory to reset the Active Directory Account password.

If the current account password is supplied then this command will use the password change operation which does not require any elevated permissions in Active Directory.


## Related Commands

* [New-AcctADAccount](./New-AcctADAccount/)
* [Add-AcctADAccount](./Add-AcctADAccount/)
* [Remove-AcctADAccount](./Remove-AcctADAccount/)
* [Unlock-AcctADAccount](./Unlock-AcctADAccount/)
* [Update-AcctADAccount](./Update-AcctADAccount/)
* [Get-AcctADAccount](./Get-AcctADAccount/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ADAccountName | The Active Directory account name(s) that are to be repaired. Active Directory accounts are accepted in the following formats: Fully qualified DN e.g. CN=MyComputer,OU=Computers,DC=MyDomain,DC=Com; UPN format e.g MyComputer@MyDomain.Com; Domain qualified e.g MyDomain\\MyComputer. | true | false |  |
| ADAccountSid | The Active Directory account SID(s) that are to be repaired. | true | true (ByPropertyName) |  |
| Password | The current  password for the computer account. | false | false |  |
| SecurePassword | The current password for the account (provided in a Secure String class). | false | false |  |
| ADUserName | The username for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| ADPassword | The matching password for an Active Directoy user account with Write Permissions. This parameter is only used in Cloud deployments. | false | false |  |
| Force | Indicates whether accounts that are marked as 'in-use' can be repaired or not. | false | false |  |
| LoggingId | Specifies the identifier of the high-level operation this cmdlet call forms a part of. Citrix Studio and Director typically create high-level operations. PowerShell scripts can also wrap a series of cmdlet calls in a high-level operation by way of the Start-LogHighLevelOperation and Stop-LogHighLevelOperation cmdlets. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snap-in connects to.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Adidentity.Sdk.Accountoperationsummary
The Repair-AcctADAccout command returns an object with the following parameters:<br>    SuccessfulAccountsCount &lt;int&gt;<br>        The number of accounts that were repaired successfully.<br>    FailedAccountsCount &lt;int&gt;<br>        The number of accounts that were not repaired.<br>    FailedAccounts &lt;Citrix.ADIdentity.Sdk.AccountError\[\]&gt;<br>        The list of accounts that failed to be repaired.  Each one has the following parameters:<br>            ADAccountName &lt;string&gt;<br>            ADAccountSid &lt;String&gt;<br>            ErrorReason &lt;ADIdentityStatus&gt;<br>              This can be one of the following<br>              UnableToConvertDomain<br>              IdentityNotLocatedInDomain<br>              IdentityNotFound<br>              IdentityObjectInUse<br>              IdentityObjectLocked<br>              ADServiceDatabaseError<br>              ADServiceDatabaseNotConfigured<br>              ADServiceStatusInvalidDb<br>              FailedToConnectToDomainController<br>              FailedToExecuteSearchInAD<br>              FailedToAccessComputerAccountInAD<br>              FailedToSetPasswordInAD<br>              FailedToChangePasswordInAD<br>            DiagnosticInformtion &lt;Exception&gt;<br>              Any other error information
## Notes
In the case of failure, the following errors can result.<br>    Error Codes<br>    -----------<br>    PermissionDenied<br>    The user does not have administrative rights to perform this operation.<br>    ConfigurationLoggingError<br>    The operation could not be performed because of a configuration logging error<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>    The operation could not be completed because the database for the service is not configured.<br>    ServiceStatusInvalidDb<br>    An error occurred in the service while attempting a database operation - communication with database failed for<br>    for various reasons.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
C:\PS>Repair-AcctADAccount -ADAccountName "Domain\account","domain\account2"

          SuccessfulAccountsCount       FailedAccountsCount    FailedAccounts

          -----------------------       -------------------    --------------

                                2                         0    {}
```
#### Description

