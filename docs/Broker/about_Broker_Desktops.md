
# about\_Broker\_Desktops

## Topic
Citrix Broker SDK - Desktops


## Short Description
Describes desktop concepts and usage.


## Long Description
A desktop is a machine that is able to run a Microsoft Windows desktop environment (with a shell, icons and taskbar) or individual applications (seamlessly integrated with the local desktop). The configuration of the desktop determines whether it can run only desktop environments, only applications, or both desktops and applications. Machines running workstation operating systems are able to run one session at a time (single-session), whereas machines running server operating systems have the ability to run multiple simultaneous sessions (multi-session).

A key aspect of desktops is how they are assigned (or allocated) to users. Two allocation types are supported:


* Random/Shared - A user is assigned a desktop at random from a pool of shared desktops. Multi-session desktops are able to run sessions to multiple users simultaneously, whereas single-session desktops can only run one session at a time, and are returned to the pool when the user logs off. Single-session shared desktops usually discard user data stored on them after the user logs off. Multi-session shared desktops, however, do not tend to discard user data after a log-off, as this is only possible when the desktop is rebooted by a reboot schedule.

* Permanent/Private - A private desktop is permanently assigned to a specific user and data stored on it is retained across logons and restarts. A private desktop can have users assigned explicitly or on first use.

### Desktop Groups

Desktops are collected together in desktop groups, and these provide a flexible grouping mechanism that can be used to associate:


* Desktops running on a particular type of machine
* Desktops with particular software installed
* Desktops for a set of users
* Desktops accessed in a similar way
* Desktops configured in a particular way
* Any combination of the above

Each desktop group can only contain one type of desktop, determined by its AllocationType and SessionSupport properties.

When assigning shared desktops or assign-on-first-use (AOFU) desktops to users, the set of candidates comes from available desktops in a particular desktop group.

You configure power management policy for single-session desktop groups, including peak and off-peak settings, for each desktop group. See about\_Broker\_PowerManagement for details.


### Creation Of Desktops
Desktop objects are created automatically when a machine is added to a desktop group. The type of desktop is determined by the AllocationType property of the desktop group.

In order for a machine to be added from a catalog, the machine must be compatible with the desktop group. For this to be true, the catalog's AllocationType must be compatible, and the SessionSupport property must match.

Note: Because the session support and functional level of the machine are determined by the software on the machine (operating system and Citrix VDA, respectively), the SessionSupport and MinimalFunctionalLevel of the catalog and desktop group may match, but not be compatible with the machine. In this case any attempt of registration by the machine will fail.

You can add machines explicitly using the Add-BrokerMachine cmdlet, or a number of free machines can be acquired from a catalog using the Add-BrokerMachinesToDesktopGroup cmdlet. A machine can only be associated with one desktop group at a time, and has a DesktopUid property that references the corresponding desktop object. You can also associate desktops to machines with their SID properties.

Desktop objects are deleted when the machine is removed from the desktop group (using the Remove-BrokerMachine cmdlet). Desktops are also deleted when the desktop group containing them is deleted (using the Remove-BrokerDesktopGroup cmdlet). A desktop cannot be removed from a catalog while it is in a desktop group.


### Shared (Random) Desktops
Shared desktops are published to users using entitlement policy rules. Each entitlement rule allows access to a single session on a desktop machine, selected at random from the available desktops in a desktop group (with a preference for desktops that are powered on). If there are no available desktops, launching the session fails. See about\_Broker\_EntitlementPolicy and about\_Broker\_PowerManagement for details.


### Private (Static) Desktops
You can assign private desktops to users explicitly or automatically, with the AOFU feature. It is also possible to assign private desktops to particular clients (through IP or client name).

You explicitly assign machines or desktops to users with the Add-BrokerUser cmdlet. Machines can be assigned to users before the machine has been added to the desktop group (desktop created), but otherwise the effect is the same.

With Add-BrokerUser you can assign a desktop to multiple users or user groups. If the desktop has single-session support then the desktop will be visible to multiple users, but only one user can log on to the desktop at any time.

Assignment policy rules allow you to use AOFU to assign desktops to users in a desktop group. When a user specified in an assignment policy rule launches a session, and if the user does not already have an assigned desktop, the broker selects an available desktop at random from the desktop group and permanently assigns it to that user. Once assigned in this way, the desktop behaves as though the assignment was made explicitly by an administrator. See about\_Broker\_AssignmentPolicy for details.

It is possible to assign more than one desktop to a user. You can achieve this by explicit assignment, multiple assignment policy rules, or the MaxDesktops property of an assignment policy rule.


## Desktop Configuration
When presented to the user, desktops are identified by:

* An icon (IconUid property)
* A name (PublishedName property)
* A description (Description property)

When starting the session, you can configure two connection settings:

* The color depth used at the start of the session (ColorDepth property)
* Whether SecureICA encryption is required (SecureIcaRequired property)

Each desktop group provides default values for these settings, but you can override them if the desktop has more specific settings (PrivateDesktop), or use an entitlement policy rule with more specific settings (SharedDesktop).

AOFU desktops can inherit these settings from the assignment policy rule when the assignment to the user takes place.


### Maintenance Mode
There are times when it is necessary to disable desktops. You can do this by setting the InMaintenanceMode property of a desktop to \$true. This puts it into maintenance mode. The broker excludes single-session desktops in maintenance mode from brokering decisions and does not start new sessions on them. Existing sessions are unaffected. For multi-session desktops in maintenance mode, reconnections to existing sessions are allowed, but no new sessions are created on the machine.

Desktops in maintenance mode are also excluded from automatic power management, although explicit power actions are still performed.

Note that disabling desktop groups, entitlement policy rules, assignment policy rules, or applications are other ways of disabling aspects of brokering.


## Desktop Status
Once desktops are created, you can query the configuration and state information for different kinds of desktop, or retrieve more information about desktops using the Get-BrokerMachine cmdlet. To get details of any sessions running on the desktops, use the Get-BrokerSession cmdlet.

You can also group desktops by a specific property, counting the number of desktops with each value using the Group-BrokerMachine cmdlet. This can provide useful summary statistics.


## Desktop Usage
Every hour the broker records how many desktops from each desktop group are in use, and the Get-BrokerDesktopUsage cmdlet returns this information. Analyze historical usage records to understand desktop usage patterns and help with the choice of idle pool and buffer settings.


## Desktop Conditions
CPU usage, ICA latency, and profile logon times of desktops are monitored. When one of these values exceeds a threshold (configured by policy), the condition is flagged in the DesktopConditions property of the desktop. When the value drops below the threshold again, the condition is cleared. Use Get-BrokerMachine or Group-BrokerMachines cmdlets to query this information.


## See Also

* [about\_Broker\_Concepts](./about_Broker_Concepts/)
* [about\_Broker\_Applications](./about_Broker_Applications/)
* [about\_Broker\_EntitlementPolicy](./about_Broker_EntitlementPolicy/)
* [about\_Broker\_AssignmentPolicy](./about_Broker_AssignmentPolicy/)
* [Add-BrokerMachine](./Add-BrokerMachine/)
* [Add-BrokerMachinesToDesktopGroup](./Add-BrokerMachinesToDesktopGroup/)
* [Remove-BrokerMachine](./Remove-BrokerMachine/)
* [Add-BrokerUser](./Add-BrokerUser/)
* [Set-BrokerMachine](./Set-BrokerMachine/)
* [Set-BrokerPrivateDesktop](./Set-BrokerPrivateDesktop/)
* [Get-BrokerMachine](./Get-BrokerMachine/)
* [Group-BrokerMachine](./Group-BrokerMachine/)
* [Get-BrokerDesktopUsage](./Get-BrokerDesktopUsage/)

