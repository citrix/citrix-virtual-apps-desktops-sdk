
# about\_Broker\_Machines

## Topic
Citrix Broker SDK - Machine Object


## Short Description
Describes machine concepts and usage.


## Long Description
A machine represents a physical or virtual machine that can be used to provide a user with one or more desktops, applications or both. When a machine is created, you must assign it to a catalog, which defines how the machine is allocated to a user (static or random), the session support it provides (single-session or multi-session), how the machine's disk images are created and managed (PVS, MCS or manually) and the expected functional level. If the machine is virtual but not provisioned by MCS, you must also assign it to a hypervisor connection, which represents the hypervisor (or pool of linked hypervisors) that runs the virtual machine.

Creating a machine object is the first step in the broker SDK towards configuring a physical or virtual machine to provide desktops and/or applications to users. A machine must be added to a desktop group before it is able to be used(see about\_Broker\_Desktops). To add machines to a desktop group, the Add-BrokerMachine or Add-BrokerMachinesToDesktopGroup cmdlets can be used. This creates a desktop object corresponding to the machine.


## Catalogs
When a machine is created, you must assign it to a catalog. The catalog defines the behavior of the machine within a site as well as the expected functionality and properties of the machine:


* Allocation type: The catalog determines how the machines are allocated to the user. Allocation can be static or random. Static allocation is where the machine is permanently assigned to a specific user. Data stored is retained across logons and restarts.
The other type of allocation is random, where a random machine is assigned to a user from a pool when a session is requested. The machine returns to the pool when the user logs off.

* How the machine is created: The catalog collects together machines that are created in the same way: either with PVS, MCS or manually.

* Physical or Virtual: A machine that is virtual can have its power state controlled and monitored by the system. Virtual machines must be associated with a hypervisor connection, either directly or, in the case of MCS provisioned machines, indirectly through the provisioning scheme. Single session virtual machines can be managed using power policy to automatically be turned on or off as needed. Machines marked as physical are not monitored or controlled as to their power state.

* How the users settings are stored: The catalog also determines how the users settings are stored, either on a Citrix Personal vDisk, on the machine’s local drive, or if the user settings are discarded.

* RemotePC: If the catalog is set up as a remote PC catalog, machines are added automatically upon registration based on the site configuration. In order for a catalog to be specified as a RemotePC catalog, the session support must be single session and the catalog must be set up for physical machines.

* Functional level: The functional level of a machine is determined by the version of the Citrix VDA software it is running. Some features are not supported in machines with lower functional levels. Catalogs can supply a minimal functional level, meaning any machines in the catalog with a lower functional level will be unable to register with the site.

* Session support: This can either be single-session or multi-session. Single-session machines can have an active session with up to one user at any time, whereas multi-session machines have the capability to have active sessions with multiple users simultaneously. The session support of a machine is determined by the variant of the VDA software component installed on the machine (either with single-session support or multi- session support). The multi-session VDA software may only be installed on server operating systems. The catalog session support must match the session support of the software installed on the machine for the machine to successfully register with the site.

## Machine Status

After machines are created, you can query the configuration and state information using the Get-BrokerMachine cmdlet. The information the cmdlet can provide includes, but is not limited to, the following:


* Personal vDisk interactions and lifecycle: The current state of the personal vDisk can be obtained, as well as the configuration options of how the user data is persisted.

* Session properties: The properties of the current session for single- session machines can be obtained, such as ClientName and ClientAddress. To access session information on multi-session machines, the Get-BrokerSession cmdlet can be used.

* Application status: If the machine is configured to run applications, information can be found about the published applications running on the machine.

* Connection information: Information about the time and user of the last connection to the machine can be found, as well as information about the last deregistration.

For an exhaustive list of the properties of a machine that can be queried, see the Get-BrokerMachine cmdlet.


## Machine Configuration
Machine settings can be changed and configured once the machine object has been created, as long as the changes are compatible with the catalog the machine is in. For example, more users can be assigned to the machine than were initially assigned when creating the machine object, this is done with the Add-BrokerUser cmdlet.

For a full list of the machine configuration options available, see the Set-BrokerMachine command.


## Maintenance Mode
There are times when it is necessary to disable machines. This can be achieved by setting the InMaintenanceMode property to \$true. This puts the machine into maintenance mode. With single-session machines, this means that the broker excludes the machine from brokering decisions and does not start new sessions on them. Existing sessions are unaffected. For multi-session desktops in maintenance mode, reconnections to existing sessions are allowed, but no new sessions are created on the machine.

Machines in maintenance mode are also excluded from automatic power management, although explicit power actions are still performed.


## See Also

* [about\_Broker\_PowerManagement](./about_Broker_PowerManagement/)
* [about\_Broker\_Desktops](./about_Broker_Desktops/)
* [New-BrokerMachine](./New-BrokerMachine/)
* [Add-BrokerMachine](./Add-BrokerMachine/)
* [Add-BrokerMachinesToDesktopGroup](./Add-BrokerMachinesToDesktopGroup/)
* [Remove-BrokerMachine](./Remove-BrokerMachine/)
* [Get-BrokerMachine](./Get-BrokerMachine/)
* [Set-BrokerMachine](./Set-BrokerMachine/)

