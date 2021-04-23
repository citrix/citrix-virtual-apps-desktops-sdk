
# Get-Applibscopedobject
Gets the details of the scoped objects for the AppLibrary Service.
## Syntax
```
Get-AppLibScopedObject [-ScopeId <Guid>] [-ScopeName <String>] [-ObjectType <ScopedObjectType>] [-ObjectId <String>] [-ObjectName <String>] [-Description <String>] [-Property <String[]>] [-ReturnTotalRecordCount] [-MaxRecordCount <Int32>] [-Skip <Int32>] [-SortBy <String>] [-Filter <String>] [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Returns a list of directly scoped objects including the names and identifiers of both the scope and object as well as the object description for display purposes.

There will be at least one result for every directly scoped object. When an object is associated with multiple scopes the output contains one result per scope duplicating the object details.

No records are returned for the All scope, though if an object is not in any scope a result with a null ScopeId and ScopeName will be returned.


## Related Commands

## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| ScopeId | Gets scoped object entries for the given scope identifier. | false | true (ByPropertyName) |  |
| ScopeName | Gets scoped object entries with the given scope name. | false | true (ByPropertyName) |  |
| ObjectType | Gets scoped object entries for objects of the given type. | false | true (ByPropertyName) |  |
| ObjectId | Gets scoped object entries for objects with the specified object identifier. | false | true (ByPropertyName) |  |
| ObjectName | Gets scoped object entries for objects with the specified object identifier. | false | true (ByPropertyName) |  |
| Description | Gets scoped object entries for objects with the specified description. | false | false |  |
| Property | Specifies the properties to be returned. This is similar to piping the output of the command through Select-Object, but the properties are filtered more efficiently at the server. | false | false |  |
| ReturnTotalRecordCount | When specified, the cmdlet outputs an error record containing the number of records available. This error record is additional information and does not affect the objects written to the output pipeline. See about\_AppLib\_Filtering for details. | false | false | False |
| MaxRecordCount | Specifies the maximum number of records to return. | false | false | 250 |
| Skip | Skips the specified number of records before returning results. Also reduces the count returned by -ReturnTotalRecordCount. | false | false | 0 |
| SortBy | Sorts the results by the specified list of properties. The list is a set of property names separated by commas, semi-colons, or spaces. Optionally, prefix each name with a + or - to indicate ascending or descending order. Ascending order is assumed if no prefix is present. | false | false | The default sort order is by name or unique identifier. |
| Filter | Gets records that match a PowerShell-style filter expression. See about\_AppLib\_Filtering for details. | false | false |  |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller the PowerShell snap-in will connect to. You can provide this as a host name or an IP address. | false | false | Localhost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Applibrary.Sdk.Scopedobject
The Get-AppLibScopedObject command returns an object containing the following properties:<br>ScopeId &lt;Guid?&gt;<br>    Specifies the unique identifier of the scope.<br>ScopeName &lt;String&gt;<br>    Specifies the display name of the scope.<br>ObjectType &lt;ScopedObjectType&gt;<br>    Type of the object this entry relates to.<br>ObjectId &lt;String&gt;<br>    Unique identifier of the object.<br>ObjectName &lt;String&gt;<br>    Display name of the object<br>Description  &lt;String&gt;<br>    Description of the object (possibly \$null if the object type does not have a description).
## Notes
If the command fails, the following errors can be returned.<br>    Error Codes<br>    -----------<br>    UnknownObject<br>        One of the specified objects was not found.<br>    PartialData<br>         Only a subset of the available data was returned.<br>    InvalidFilter<br>        A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    CouldNotQueryDatabase<br>         The query required to get the database was not defined.<br>    DatabaseError<br>        An error occurred in the service while attempting a database operation.<br>    DatabaseNotConfigured<br>        The operation could not be completed because the database for the service is not configured.<br>    DataStoreException<br>        An error occurred in the service while attempting a database operation - communication with the database failed for various reasons.<br>    PermissionDenied<br>        You do not have permission to execute this command.<br>    AuthorizationError<br>        There was a problem communicating with the Citrix Delegated Administration Service.<br>    CommunicationError<br>        There was a problem communicating with the remote service.<br>    ExceptionThrown<br>        An unexpected error occurred.  For more details, see the Windows event logs on the controller or the XenDesktop logs.
## Examples

### Example 1
```
c:\PS>Get-AppLibScopedObject -ObjectType Scheme

ScopeId     : eff6f464-f1ee-4442-add3-99982e0cec01

ScopeName   : Sales

ObjectType  : Scheme

ObjectId    : cd4174ee-9e4b-4e57-b126-9dbf757fe493

ObjectName  : MyExampleScheme

Description : Test scheme

ScopeId     : 304e0fa7-d390-47f0-a94f-7e956a324c41

ScopeName   : Finance

ObjectType  : Scheme

ObjectId    : cd4174ee-9e4b-4e57-b126-9dbf757fe493

ObjectName  : MyExampleScheme

Description : Test scheme

ScopeId     :

ScopeName   :

ObjectType  : Scheme

ObjectId    : 5062e46b-71bc-4ac9-901a-30fe6797e2f6

ObjectName  : AnotherScheme

Description : Another scheme in no scopes
```
#### Description
Gets all of the scoped objects with type Scheme. The example output shows a scheme object (MyExampleScheme) in two scopes Sales and Finance, and another scheme (AnotherScheme) that is not in any scope. The ScopeId and ScopeName values returned are null in the final record.
