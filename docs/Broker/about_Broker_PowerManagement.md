
# about\_Broker\_PowerManagement

## Topic
Citrix Broker SDK - Machine Power Management


## Short Description
Describes power management of machines used for desktops and applications.


## Long Description
The Citrix Broker Service is in day-to-day control of the power state of the configured desktop and application machines. The Broker Service can control several hypervisors, each hypervisor connection being handled by its own site service, so all Broker Service communication to the hypervisor is through one of the controllers in the site.


## Hypervisor Connections
Each hypervisor, or pool of linked hypervisors, is described and configured through the XdHyp pseudo-drive and associated Hyp PowerShell commands (cmdlets) which are provided by the host service snap-in. When you have first created the hypervisor connection using the host service cmdlets, you can create a broker equivalent object that references the Hyp instance using a GUID value. Use the broker's HypervisorConnection object to nominate a preferred controller for direct communication with the hypervisor on behalf of all other controllers for day-to-day power actions and status requests.


## Power Actions And Throttling
The site, through the Broker Service, can control the power state of the machines used by the site for desktops and applications. Power state changes can have a number of causes:


* Power policy rules, such as requests to shut down or suspend machines when user sessions on those machines end or are disconnected
* If allowed, user-driven desktop restarts
* Session launch requests requiring machines to be started
* Pool size management, which controls the number of running machines
* Direct administrator request using the SDK or Citrix Studio
* Reboot schedules and cycles
* Performing personal vDisk inventory activities
* Cleaning machines back to the golden master image state after they have been used

The power state changes of machines hosting desktops and applications are controlled using a queuing mechanism. Actions to change the power state are assigned a priority and are sent to the hypervisor according to a throttling mechanism. This avoids overloading the hypervisor.

The queuing and throttling mechanisms take place on a per-hypervisor-connection basis; each hypervisor connection's queue is dealt with independently. You can view the contents of the queues using the Get-BrokerHostingPowerAction cmdlet. This includes recently completed, in-progress, and pending actions (that is, those due to be sent to the hypervisor based on the throttling settings).

Each power action object comprises:


* The machine to be acted on (Name, DNS Name, Hosting Name)
* The action to be performed (TurnOn, TurnOff, Shutdown, Reset, Restart, Suspend, or Resume)
* The action's priority (Base, the original priority, and Actual, the current priority)
* The action's state (Pending, Started, Completed, Failed, Canceled, Deleted, or Lost)
* Time stamps of the action's lifecycle points (when it was created, started, or completed)
* Any reason the action failed

The throttling of power actions is controlled by three metadata values on the Hyp hypervisor connection object when accessed through the XdHyp pseudo-drive. The four values throttle power actions according to:


* The maximum absolute number of in-progress power actions
* The maximum number of in-progress power actions expressed as a percentage of the total number of machines controlled by the hypervisor connection
* The maximum number of new power actions sent to the hypervisor per minute
* The maximum number of in-progress PvD inventory activities expressed as a percentage of the total number of machines controlled by the hypervisor connection

You add power actions to the queue using the SDK's New-BrokerHostingPowerAction cmdlet. You cancel power actions in the queue using the Remove-BrokerHostingPowerAction cmdlet. You boost or reduce their priority using the Set-BrokerHostingPowerAction cmdlet.

You can also schedule power actions to be executed in the future, using the New-BrokerDelayedHostingPowerAction command. Only Shutdown and Suspend actions can be scheduled in this way. You can view these delayed power actions using Get-BrokerDelayedHostingPowerAction and cancel them with Remove-BrokerDelayedHostingPowerAction. When a delayed power action is ready to be executed it is deleted, and a corresponding normal power action is placed in the queue described above.


## Power Policy
Policy rules associated with a desktop group allow you to change power states at configurable times after session state changes, typically a set number of minutes after session disconnection or session logout.

Note that these policy rules are defined directly as properties of the desktop group.

These policy actions allow the following operations to be specified:


* A power action to be performed at a defined period after a session is disconnected
* A power action to be performed at a defined extended period after a session is disconnected
* A power action to be performed at a defined period after a session is logged off

The two disconnect policy actions are designed to allow multi-stage policies such as initially suspending a machine shortly after a session disconnect occurs, and then later powering-off the machine if the session has not been reconnected.

At the set time after the session state change, the required action is added to the power action queue, and this is then throttled and processed as normal.


## Pool Size Management
You can manage flexibly the number of machines running desktops and applications using the pool size. For any given hour of the day and day of the week, this is an absolute number of machines or the percentage of the total number of machines in the desktop group. The pool size specifies the total number of machines that are always running, regardless of whether they are in use or idle. (Note: The number of machines does not depend on their idle status, but this does affect the buffer size value, which is also used to manage pool sizes.)

To start or shut down desktop machines to achieve the desired pool size, the system places power actions in the queue. Standard throttling queue management sends these to the hypervisors. A single desktop group (and its pool) can span multiple hypervisors, so actions to start and shut down machines can be added to multiple queues.


### Power Time Schemes
Each single-session desktop group can be associated with one or more power time schemes, each scheme covering a number of days of the week. The time schemes specify, for each hour of the day, whether that hour is peak or off-peak. They also specify the number of running unassigned machines maintained by the broker.

You can configure other settings, such as buffer size and any power policy rules differently for peak and off-peak hours. You can define the number of running machines, idle or in use, either as an absolute value or as a percentage of the desktop group size. Machines running desktops and applications are started (or shut down when not in use) to match the required pool size.

Each power time scheme comprises:


* The name of the scheme
* The pattern of days of the week covered by the scheme
* The set of hours considered peak and off peak
* The set of pool size values (one for each hour of the day)

The hours of the day used by time schemes are the hours in the time zone for the desktop group the scheme is associated with. You cannot associate one desktop group with multiple time schemes covering the same day of the week.


### Buffer Size
In addition to the pool size, you can optionally configure two buffer sizes for each desktop group, one for peak hours and one for off-peak hours. The buffer size defines the minimum number of idle unassigned machines maintained by the broker and is specified as a percentage of the total machines in the group. These are running machines that are not used by any user session. The buffer size on its own never causes machines to shut down. It causes them to start up so a minimum number of idle machine is always available. The buffer size in conjunction with the pool size can cause machines running desktops or applications to be shut down.


### Power Management Of Assigned Machines
Automatic power management for private desktop groups provides the ability to power on all assigned machines at the transition to a peak period and respectively power off all machines at the transition to an off-peak period.

If a machine is shut down during peak hours it will not be automatically powered on again, unless the AutomaticPowerOnForAssignedDuringPeak property on the desktop group is also enabled.

Note that all power management facilities apply only to single session machines.


## Reboot Schedules
Reboot schedules are commonly used after image updates or to perform regular reboots of all machines in a desktop group or catalog to clear down problems resulting from a corrupt state or hung/faulty applications.

Reboot schedules allow distributing the reboot operation of all machines over a provided duration. Individual machine reboots are scheduled in a way that attempts to maintain maximum availability of machines in the group as the reboots occur, and avoid boot storms that overload the underlying infrastructure.

Reboot schedules are the only form of automatic power management that can shut down a machine while users are logged on; however the administrator can provide a warning message to be displayed to end users at a specified period prior to the shutdown taking effect.


### Reboot Cycles
Reboot cycles describe the dynamic execution of desktop group or catalog reboot operations. Reboot cycles can be created due to reboot schedules, or by on-demand reboot operations requested via the SDK.

RebootCycle objects encapsulate the details of the associated reboot operation and can be queried to show the current status.


## Status
You can view the status of the hypervisor connection on the broker hypervisor connection object. You can obtain any hypervisor alerts using the Get-BrokerHypervisorAlert cmdlet. You can check the power state of machines running desktops or applications using the relevant Machine or Desktop objects.


## See Also

* [about\_Broker\_Concepts](./about_Broker_Concepts/)
* [about\_Broker\_Machines](./about_Broker_Machines/)
* [about\_HypHostSnapin](./about_HypHostSnapin/)
* [New-BrokerHypervisorConnection](./New-BrokerHypervisorConnection/)
* [Get-BrokerHypervisorConnection](./Get-BrokerHypervisorConnection/)
* [Set-BrokerHypervisorConnection](./Set-BrokerHypervisorConnection/)
* [Remove-BrokerHypervisorConnection](./Remove-BrokerHypervisorConnection/)
* [New-BrokerHostingPowerAction](./New-BrokerHostingPowerAction/)
* [Get-BrokerHostingPowerAction](./Get-BrokerHostingPowerAction/)
* [Set-BrokerHostingPowerAction](./Set-BrokerHostingPowerAction/)
* [Remove-BrokerHostingPowerAction](./Remove-BrokerHostingPowerAction/)
* [New-BrokerDelayedHostingPowerAction](./New-BrokerDelayedHostingPowerAction/)
* [Get-BrokerDelayedHostingPowerAction](./Get-BrokerDelayedHostingPowerAction/)
* [Remove-BrokerDelayedHostingPowerAction](./Remove-BrokerDelayedHostingPowerAction/)
* [New-BrokerPowerTimeScheme](./New-BrokerPowerTimeScheme/)
* [Get-BrokerPowerTimeScheme](./Get-BrokerPowerTimeScheme/)
* [Set-BrokerPowerTimeScheme](./Set-BrokerPowerTimeScheme/)
* [Rename-BrokerPowerTimeScheme](./Rename-BrokerPowerTimeScheme/)
* [Remove-BrokerPowerTimeScheme](./Remove-BrokerPowerTimeScheme/)
* [Get-BrokerRebootCycle](./Get-BrokerRebootCycle/)
* [Set-BrokerRebootCycleMetadata](./Set-BrokerRebootCycleMetadata/)
* [Start-BrokerRebootCycle](./Start-BrokerRebootCycle/)
* [Stop-BrokerRebootCycle](./Stop-BrokerRebootCycle/)
* [Get-BrokerRebootSchedule](./Get-BrokerRebootSchedule/)
* [Set-BrokerRebootSchedule](./Set-BrokerRebootSchedule/)
* [New-BrokerRebootSchedule](./New-BrokerRebootSchedule/)
* [Remove-BrokerRebootSchedule](./Remove-BrokerRebootSchedule/)
* [New-BrokerDesktopGroup](./New-BrokerDesktopGroup/)
* [Get-BrokerDesktopGroup](./Get-BrokerDesktopGroup/)
* [Set-BrokerDesktopGroup](./Set-BrokerDesktopGroup/)
* [Add-HypMetadata](./Add-HypMetadata/)
* [Remove-HypMetadata](./Remove-HypMetadata/)

