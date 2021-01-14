
# Get-Hyphypervisorplugin
Gets the available hypervisor types.
## Syntax
```
Get-HypHypervisorPlugin [-BearerToken <String>] [-VirtualSiteId <String>] [-AdminAddress <String>] [<CommonParameters>]
```
## Detailed Description
Use this command to retrieve a list of all the available hypervisor types, and their localized names.


## Related Commands

* [New-Item](./New-Item/)
## Parameters
| Name   | Description | Required? | Pipeline Input | Default Value |
| --- | --- | --- | --- | --- |
| BearerToken | Specifies the bearer token assigned to the calling user | false | false |  |
| VirtualSiteId | Specifies the virtual site the PowerShell snap-in will connect to. | false | false |  |
| AdminAddress | Specifies the address of a XenDesktop controller to which the PowerShell snap-in connects.  You can provide this as a host name or an IP address. | false | false | LocalHost. Once a value is provided by any cmdlet, this value becomes the default. |

## Input Type

### 

## Return Values

### Citrix.Host.Sdk.Hypervisorplugin
Get-HypHypervisorPlugin returns a list of objects containing the definition of the hypervisor plug-ins.<br>    ConnectionType &lt;Citrix.XDInterServiceTypes.ConnectionType&gt;<br>        The hypervisor connection type.  This can be one of the following:<br>            XenServer - XenServer hypervisor<br>            SCVMM - Microsoft SCVMM/Hyper-V<br>            vCenter - VMWare vSphere/ESX<br>            Custom - a third-party hypervisor<br>    DisplayName &lt;string&gt;<br>        The localized display name (localized using the locale of the Powershell snap-in session)<br>    PluginFactoryName &lt;string&gt;<br>        The name of the hypervisor plug-in factory used to manage the hypervisor connections.
## Notes
To use third-party plug-ins, the plug-in assemblies must be installed into the appropriate location on each controller machine that forms part of the Citrix controller site.  Failure to do this can result in unpredictable behavior, especially during service failover conditions.<br>    In the case of failure the following errors can result.<br>    Error Codes<br>    -----------<br>    DatabaseError<br>    An error occurred in the service while attempting a database operation.<br>    CommunicationError<br>    An error occurred while communicating with the service.<br>    InvalidFilter<br>    A filtering expression was supplied that could not be interpreted for this cmdlet.<br>    ExceptionThrown<br>    An unexpected error occurred.  To locate more details, see the Windows event logs on the controller being used or examine the XenDesktop logs.
## Examples

### Example 1
```
c:\PS> Get-HypHypervisorPlugin | Format-Table -AutoSize

          ConnectionType DisplayName              PluginFactoryName

          -------------- -----------              -----------------

                   SCVMM Microsoft virtualization MicrosoftPSFactory

                 VCenter VMware virtualization    VmwareFactory

               XenServer Citrix Hypervisor        XenFactory
```
#### Description
Get the available hypervisor management plug-ins.
