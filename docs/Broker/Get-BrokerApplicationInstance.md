
# Get-Brokerapplicationinstance
Gets the running applications on the desktops.
## Syntax
```
Get-BrokerApplicationInstance -Uid <Int64> [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]

Get-BrokerApplicationInstance [-ApplicationName <String>] [-ApplicationUid <Int32>] [-ApplicationUUID <Guid>] [-Instances <Int32>] [-MachineName <String>] [-MachineUid <Int32>] [-Metadata <String>] [-SessionKey <Guid>] [-SessionUid <Int64>] [-UserName <String>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-Property <String[]>] [-AdminAddress <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [<CommonParameters>]
```
## Detailed Description
The Get-BrokerApplicationInstance gets the published applications that are running on desktops.

Only published applications that are launched from a Citrix client are returned. If a user launches an application from within a session (by double-clicking on an attachment from an email, for example) this will not show up in the list of running applications.

Also note that this is a list of launched published applications, not a list of processes running on the desktop. In some cases the original process associated with the published application may no longer be running, but if the session is still running the published application may be listed as running.

The number of instances for each published application running in a session is also returned. For example, if a user launches two Notepad applications from a Citrix client, and session-sharing occurs such that both Notepad applications run in the same session, then the Instances property indicates that 2 copies are running in the session.

See Get-BrokerApplication and Get-BrokerSession to get the details for the applications and sessions, respectively.

The Get-BrokerMachine cmdlet also returns a list of published applications that are running on a desktop. See the "ApplicationsInUse" attribute of the returned desktop objects.


### Brokerapplicationinstance Object
The BrokerApplicationInstance object represents an instance of a published application in the site. It contains the following properties:


  * ApplicationName (System.String) The administrative name of the application.

  * ApplicationUid (System.Int32) The UID of the application.

  * ApplicationUUID (System.Guid) The UUID of the application.

  * Instances (System.Int32) The number of times this published application is running in the specified session.

  * MachineName (System.String) Machine's SAM name (of the form domain\\machine). If SAM name is unavailable, contains the machines's SID.

  * MachineUid (System.Int32) UID of underlying machine.

  * MetadataMap (System.Collections.Generic.Dictionary&lt;string, string&gt;) Metadata for this application instance.

  * SessionKey (System.Guid) The key of the session.

  * SessionUid (System.Int64) The UID of the session.

  * Uid (System.Int64) The unique identifier for this application instance object itself, distinct from the Uids of either application or session. objects.

  * UserName (System.String) User name (SAMName).


## Related Commands

* [Get-BrokerApplication](./Get-BrokerApplication/)
* [Get-BrokerDesktop](./Get-BrokerDesktop/)
* [Get-BrokerSession](./Get-BrokerSession/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| Uid | Gets only the application instances specified by the unique identifier. This is the unique identifier for the application instance object itself, and is distinct from the Uids of either application or session objects. | true | false |  |
| ApplicationName | Gets only application instances for the specified application name. | false | false |  |
| ApplicationUid | Gets only application instances for the specified application Uid. | false | false |  |
| ApplicationUUID | Gets only the application instances for the specified application UUID. | false | false |  |
| Instances | Gets only application instances that match the specified number of instances. | false | false |  |
| MachineName | Gets only application instances running on the specified machines. | false | false |  |
| MachineUid | Gets only application instances running on the machine with the specified UID. | false | false |  |
| Metadata | Gets records with matching metadata entries.<br>The value being compared with is a concatenation of the key name, a colon, and the value. For example: -Metadata "abc:x\*" matches records with a metadata entry having a key name of "abc" and a value starting with the letter "x". | false | false |  |
| SessionKey | Gets only application instances for the published applications running in the specified session. | false | false |  |
| SessionUid | Gets only application instances for the published applications running in the specified session. | false | false |  |
| UserName | Gets only application instances being run by the specified users. | false | false |  |
| ReturnTotalRecordCount | When specified, this causes the cmdlet to output an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_Broker\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell style filter expression. See about\_Broker\_Filtering for details. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller that the PowerShell snapin will connect to. This can be provided as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value will become the default. |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |

## Input Type

### None
You cannot pipe input into this cmdlet.
## Return Values

### Citrix.Broker.Admin.Sdk.Applicationinstance
Get-BrokerApplicationInstance returns an object for each application instance it gets.
## Examples

### Example 1
```
C:\PS> Get-BrokerApplicationInstance -Uid 3
```
#### Description
Returns the application instance with a Uid of 3. Note that this is the unique identifier for application instances, which is distinct from the unique identifiers of either application or session objects.
### Example 2
```
C:\PS> $app = Get-BrokerApplication Notepad

C:\PS> Get-BrokerApplicationInstance -ApplicationUid $app.Uid
```
#### Description
Returns all the application instances for the Notepad application. Use this to see if there are any launched instances of Notepad running in your site and, if so, from which desktops.
### Example 3
```
C:\PS> $sessions = Get-BrokerSession -MachineName "ACME\Worker1"

C:\PS> for ($i=0; $i -lt $sessions.Length; $i++) {

            Get-BrokerApplicationInstance -SessionUid $sessions[$i].SessionUid

          }
```
#### Description
Returns all the applications that are running on the "Worker1" machine in the "ACME" domain. Use this to see which published applications are running on a specific machine.&lt;br&gt;Note that the SessionUid, not the SessionId, is specified as a parameter to this cmdlet. The SessionId is a unique identifier that Remote Desktop Services uses to track the session, and is unique only on that machine. The SessionUid, on the other hand, is unique across the entire site.&lt;br&gt;The "ApplicationsInUse" attribute of the returned session object also provides a list of running launched applications, and in many cases might be more convenient to use. It returns a list of application BrowserNames.
