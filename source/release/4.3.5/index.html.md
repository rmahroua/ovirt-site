---
title: oVirt 4.3.5 Release Notes
category: documentation
layout: toc
authors: sandrobonazzola
---

# oVirt 4.3.5 Release Notes

The oVirt Project is pleased to announce the availability of the 4.3.5 Fifth Release Candidate as of July 11, 2019.

oVirt is an open source alternative to VMware™ vSphere™, providing an
awesome KVM management interface for multi-node virtualization.
This release is available now for Red Hat Enterprise Linux 7.6,
CentOS Linux 7.6 (or similar).


To find out how to interact with oVirt developers and users and ask questions,
visit our [community page]"(/community/).
All issues or bugs should be reported via
[Red Hat Bugzilla](https://bugzilla.redhat.com/enter_bug.cgi?classification=oVirt).
The oVirt Project makes no guarantees as to its suitability or usefulness.
This pre-release should not to be used in production, and it is not feature
complete.


For a general overview of oVirt, read the [Quick Start Guide](/documentation/quickstart/quickstart-guide/)
and visit the [About oVirt](/documentation/introduction/about-ovirt/) page.

For detailed installation instructions, read the [Installation Guide](/documentation/install-guide/Installation_Guide/).

To learn about features introduced before 4.3.5, see the [release notes for previous versions](/documentation/#previous-release-notes).


## Install / Upgrade from previous versions

### CentOS / RHEL


## RELEASE CANDIDATE

In order to install this Release Candidate you will need to enable pre-release repository.




In order to install it on a clean system, you need to install


`# yum install `[`http://resources.ovirt.org/pub/yum-repo/ovirt-release43-pre.rpm`](http://resources.ovirt.org/pub/yum-repo/ovirt-release43-pre.rpm)


and then follow our
[Installation Guide](http://www.ovirt.org/documentation/install-guide/Installation_Guide/).



### oVirt Hosted Engine

If you're going to install oVirt as a Hosted Engine on a clean system please
follow [Hosted_Engine_Howto#Fresh_Install](/documentation/how-to/hosted-engine/#fresh-install)
guide or the corresponding section in
[Self Hosted Engine Guide](/documentation/self-hosted/Self-Hosted_Engine_Guide/).

If you're upgrading an existing Hosted Engine setup, please follow
[Hosted_Engine_Howto#Upgrade_Hosted_Engine](/documentation/how-to/hosted-engine/#upgrade-hosted-engine)
guide or the corresponding section within the
[Upgrade Guide](/documentation/upgrade-guide/upgrade-guide/).

### EPEL

Don't enable all of EPEL on oVirt machines.

The ovirt-release package enables the EPEL repositories and includes several
specific packages that are required from there. It also enables and uses
the CentOS SIG repos, for other packages.

If you want to use other packages from EPEL, you should make sure to
use `includepkgs` and add only those you need avoiding to override
packages from other repos.


## What's New in 4.3.5?

### Release Note

#### oVirt Engine

 - [BZ 1706804](https://bugzilla.redhat.com/1706804) <b>Require WildFly 17 for oVirt Engine 4.3</b><br>oVirt engine 4.3.5 now depends on WildFly 17.0.0.FINAL

#### oVirt Release Package

 - [BZ 1718162](https://bugzilla.redhat.com/1718162) <b>Switch to glusterfs 6 repositories</b><br>oVirt Release package is now providing repository configuration for Glusterfs 6.<br>You can find more information about how to upgrade gluster to version 6 at https://docs.gluster.org/en/latest/Upgrade-Guide/upgrade_to_6/

### Enhancements

#### oVirt Engine

 - [BZ 1723580](https://bugzilla.redhat.com/1723580) <b>[downstream clone - 4.3.5] [RFE] Support console VNC for mediated devices</b><br>
 - [BZ 1711795](https://bugzilla.redhat.com/1711795) <b>[downstream clone - 4.3.5] [RFE][UI] Provide information about the VM next run</b><br>Feature: <br>A list of the names of changed fields between current and next run of the virtual machine is now displayed in the tooltip of the vm type icon on the VM list page. <br>Reason: <br>Until now, it was not possible to see which fields have been changed. <br>Result:<br>User can see the names of changed fields.
 - [BZ 1704647](https://bugzilla.redhat.com/1704647) <b>Cannot import OVA as template (Failed to query OVA info)</b><br>Feature: When attempting to import OVA files as a Template when only one or more VM OVA files exists and no Template OVA files exist, the Import gave an error message that the Import failed to load the OVA file from the directory. It was not clear that the failure was due to failing to find a compatible OVA file in the directory. The wording of the message was therefore modified so that it was clearer to the user.<br><br>Reason: Users felt the message was confusing.<br><br>Result: The message now reports that the process failed to find or load the OVA file which covers both scenarios.
 - [BZ 1683965](https://bugzilla.redhat.com/1683965) <b>[RFE] Option to create a VM with VNC console and without any USB device</b><br>
 - [BZ 1719735](https://bugzilla.redhat.com/1719735) <b>[downstream clone - 4.3.5] [RFE] Add by default a storage lease to HA VMs</b><br>Feature: When HA is selected for a New VM we now set the Lease Storage Domain to a bootable Storage Domain automatically if the user did not already choose one.<br><br>Reason: To protect new HA VMs with leases when it has a bootable Storage Domain.<br><br>Result: Now a bootable Storage Domain is set as the lease Storage Domain for new HA VMs.
 - [BZ 1712353](https://bugzilla.redhat.com/1712353) <b>[downstream clone - 4.3.5] [RFE] Allow Maintenance of Host with Enforcing VM Affinity Rules (hard affinity)</b><br>

#### VDSM

 - [BZ 1715608](https://bugzilla.redhat.com/1715608) <b>[downstream clone - 4.3.5] [RFE] Create a VDSM hook to pass host disks as disk devices (today we support passing them as SCSI-generic devices)</b><br>hostdev_scsi Vdsm hook has been added, to transform some SCSI host devices for better performance.<br><br>See https://github.com/oVirt/vdsm/blob/master/vdsm_hooks/hostdev_scsi/README for more details.

#### oVirt Hosted Engine HA

 - [BZ 1659052](https://bugzilla.redhat.com/1659052) <b>[RFE] Consider alternative to ICMP ping for hosted engine network test</b><br>Feature: Currently the virtualization host checks it's network liveliness by pinging the gateway. Alternative ways of checking network connectivity are added.<br><br>Reason: In some scenarios, the gateway does not reply to ping, e.g. if ping is blocked on network level.<br><br>Result: During the installation of hosted engine, the admin can configure the way the network connectivity is checked. The options to choose are a check if the DNS resolution is working, ping the gateway, TCP connection to a configurable port on a configurable host, or no check at all.<br><br>https://github.com/oVirt/ovirt-site/pull/1985

#### oVirt Hosted Engine Setup

 - [BZ 1659052](https://bugzilla.redhat.com/1659052) <b>[RFE] Consider alternative to ICMP ping for hosted engine network test</b><br>Feature: Currently the virtualization host checks it's network liveliness by pinging the gateway. Alternative ways of checking network connectivity are added.<br><br>Reason: In some scenarios, the gateway does not reply to ping, e.g. if ping is blocked on network level.<br><br>Result: During the installation of hosted engine, the admin can configure the way the network connectivity is checked. The options to choose are a check if the DNS resolution is working, ping the gateway, TCP connection to a configurable port on a configurable host, or no check at all.<br><br>https://github.com/oVirt/ovirt-site/pull/1985

#### OTOPI

 - [BZ 1694423](https://bugzilla.redhat.com/1694423) <b>[RFE] disable dnf by default on EL7</b><br>OTOPI's DNF packager and minidnf is now disabled on EL7 by default, even if dnf is installed. To enforce otopi to try it, add to the relevant tool's (e.g. engine-setup) answer file:<br><br>PACKAGER/dnfpackagerEnabled=bool:True<br><br>Or add this to the system environment (e.g. 'export' from the shell):<br><br>OTOPI_DNF_ENABLE=1<br><br>(Former is stronger. If set to False, latter won't have any effect).

#### oVirt Engine UI Extensions

 - [BZ 1712353](https://bugzilla.redhat.com/1712353) <b>[downstream clone - 4.3.5] [RFE] Allow Maintenance of Host with Enforcing VM Affinity Rules (hard affinity)</b><br>

### Rebase: Bug Fixeses and Enhancementss

#### oVirt Engine

 - [BZ 1710696](https://bugzilla.redhat.com/1710696) <b>[downstream clone - 4.3.5] [RESTAPI] Adding ISO disables serial console</b><br>

### Bug Fixes

#### oVirt Engine

 - [BZ 1725660](https://bugzilla.redhat.com/1725660) <b>[downstream clone - 4.3.5] Cannot retrieve Host NIC VF configuration via REST API</b><br>
 - [BZ 1709201](https://bugzilla.redhat.com/1709201) <b>Change md5 checksum used in GlusterHooks calls</b><br>
 - [BZ 1693571](https://bugzilla.redhat.com/1693571) <b>[v2v] VMware UEFI VM is imported as i440fx/seabios instead of q35/ovmf</b><br>
 - [BZ 1674352](https://bugzilla.redhat.com/1674352) <b>[RFE] Block changing the Initial Run configuration in a VM-Pool</b><br>
 - [BZ 1638674](https://bugzilla.redhat.com/1638674) <b>[Dalton] Optimize for virt store fails with distribute volume type</b><br>
 - [BZ 1721362](https://bugzilla.redhat.com/1721362) <b>[downstream clone - 4.3.5] Third VM fails to get migrated when host is placed into maintenance mode</b><br>
 - [BZ 1697682](https://bugzilla.redhat.com/1697682) <b>'Error processing event data' errors seen in engine.log</b><br>
 - [BZ 1720110](https://bugzilla.redhat.com/1720110) <b>Unable to edit pool that is delete protected</b><br>
 - [BZ 1630824](https://bugzilla.redhat.com/1630824) <b>engine-backup should backup ovirt-provider-ovn</b><br>
 - [BZ 1716951](https://bugzilla.redhat.com/1716951) <b>[downstream clone - 4.3.5] Highly Available (HA) VMs with a VM lease failed to start after a 4.1 to 4.2 upgrade.</b><br>
 - [BZ 1699684](https://bugzilla.redhat.com/1699684) <b>vm_init wiped on cluster level upgrade</b><br>

#### VDSM

 - [BZ 1725390](https://bugzilla.redhat.com/1725390) <b>ovirt-engine 4.3.5-2 fails to add disk/update OVF/deactivate SD on a storage domain which resides on a 4.1 compatibility level cluster: InvalidParameterException: Invalid parameter: 'DiskType=2</b><br>
 - [BZ 1709201](https://bugzilla.redhat.com/1709201) <b>Change md5 checksum used in GlusterHooks calls</b><br>
 - [BZ 1723873](https://bugzilla.redhat.com/1723873) <b>[downstream clone - 4.3.5] ovirt-engine-4.1.11.2 fails to add disks with vdsm-4.30 hosts and 4.1 compatibility level: InvalidParameterException: Invalid parameter: 'DiskType=2'</b><br>

#### oVirt Cockpit Plugin

 - [BZ 1703678](https://bugzilla.redhat.com/1703678) <b>Passwords saved in clear-text variable files during HE deployment via cockpit-ovirt</b><br>

#### oVirt Hosted Engine Setup

 - [BZ 1721362](https://bugzilla.redhat.com/1721362) <b>[downstream clone - 4.3.5] Third VM fails to get migrated when host is placed into maintenance mode</b><br>
 - [BZ 1665934](https://bugzilla.redhat.com/1665934) <b>Host stuck in preparing to maintenance - operation failed: migration job: unexpectedly failed</b><br>
 - [BZ 1691244](https://bugzilla.redhat.com/1691244) <b>[scale] HE - unable to migrate HE vm by putting the host to maintenance</b><br>

#### oVirt Ansible hosted-engine setup role

 - [BZ 1725033](https://bugzilla.redhat.com/1725033) <b>Hosted engine re-deploys failed since libvirt network subnet is already in used.</b><br>

### Other

#### VDSM JSON-RPC Java

 - [BZ 1710818](https://bugzilla.redhat.com/1710818) <b>Connection to host is stucked and host stays NonResponsive until engine restart</b><br>

#### oVirt Engine

 - [BZ 1723578](https://bugzilla.redhat.com/1723578) <b>[downstream clone - 4.3.5] Increase of ClusterCompatibilityVersion to Cluster with virtual machines with outstanding configuration changes, those changes will be reverted</b><br>
 - [BZ 1535322](https://bugzilla.redhat.com/1535322) <b>[UI] - Networks - Add info tooltip (blue i icon) next to the 'Custom' field in the External section</b><br>
 - [BZ 1727521](https://bugzilla.redhat.com/1727521) <b>DWH admin portal dashboard queries use 4.2 views</b><br>
 - [BZ 1688982](https://bugzilla.redhat.com/1688982) <b>[IPv6] REST API incorrectly reports the address of an NFS storage domain if it contains an IPv6 address</b><br>
 - [BZ 1725620](https://bugzilla.redhat.com/1725620) <b>upload image fails for small qcow images on file domains</b><br>
 - [BZ 1535324](https://bugzilla.redhat.com/1535324) <b>[UI] - Networks - Align the whole text in the External section to the left</b><br>
 - [BZ 1701736](https://bugzilla.redhat.com/1701736) <b>files within a qemu vm  on glusterfs are randomly overwritten by Zero Bytes</b><br>
 - [BZ 1590866](https://bugzilla.redhat.com/1590866) <b>SDK allows to create template in one DC with disk in another DC</b><br>
 - [BZ 1673035](https://bugzilla.redhat.com/1673035) <b>[cinderlib] Support snapshot operations</b><br>
 - [BZ 1683566](https://bugzilla.redhat.com/1683566) <b>[CinderLib] Webadmin- managed block disks of VM template are not aligned in Templates-> Disks table</b><br>
 - [BZ 1728210](https://bugzilla.redhat.com/1728210) <b>[downstream clone - 4.3.5] VM is going to pause state with "storage I/O  error".</b><br>
 - [BZ 1723582](https://bugzilla.redhat.com/1723582) <b>[downstream clone - 4.3.5] RHV could not detect Guest Agent when create snapshot for the running guest which installed qemu-guest-agent</b><br>
 - [BZ 1722026](https://bugzilla.redhat.com/1722026) <b>no tablet device for SPICE+VNC defined</b><br>
 - [BZ 1590218](https://bugzilla.redhat.com/1590218) <b>Deletion of snapshot ends with failure</b><br>
 - [BZ 1719737](https://bugzilla.redhat.com/1719737) <b>[downstream clone - 4.3.5] Cannot disable SCSI passthrough using API</b><br>
 - [BZ 1719332](https://bugzilla.redhat.com/1719332) <b>Change default gluster mount point to /gluster_bricks</b><br>
 - [BZ 1722235](https://bugzilla.redhat.com/1722235) <b>[downstream clone - 4.3.5] VM not started on the expected host since external weight policy units are ignored.</b><br>
 - [BZ 1721073](https://bugzilla.redhat.com/1721073) <b>Run metrics ansible role only if the ovirt-engine-metrics rpm installed</b><br>
 - [BZ 1616327](https://bugzilla.redhat.com/1616327) <b>UI plugin contributed buttons in main view aren't reflected into detail view</b><br>
 - [BZ 1533362](https://bugzilla.redhat.com/1533362) <b>StreamingAPI - successful cancel Upload/Download disk via UI  should not finish as an ERROR in Engine.log/UI event log as this was requested by user & completed successfully</b><br>
 - [BZ 1697496](https://bugzilla.redhat.com/1697496) <b>"attach_volume error=Managed Volume is already attached." when migrating VM with Managed Block Storage (Ceph RBD)</b><br>
 - [BZ 1715877](https://bugzilla.redhat.com/1715877) <b>[downstream clone - 4.3.5] engine-setup should check for snapshots in unsupported CL</b><br>Now, on upgrade, engine-setup prompts about virtual machines that have snapshots that are incompatible with the version we are going to upgrade to. It's safe to let it proceed, but it's not safe to try using these snapshots after the upgrade, e.g. to preview them.
 - [BZ 1494531](https://bugzilla.redhat.com/1494531) <b>removing datacenter keep nfs mounted</b><br>
 - [BZ 1648623](https://bugzilla.redhat.com/1648623) <b>[UI] Warn that bond names >10 may explode with vlan</b><br>
 - [BZ 1717538](https://bugzilla.redhat.com/1717538) <b>[CodeChange][i18n] oVirt 4.3 webadmin - revert pt-BR translations</b><br>
 - [BZ 1651874](https://bugzilla.redhat.com/1651874) <b>Live merge failed with NPE on endAction of DestroyImage</b><br>
 - [BZ 1713371](https://bugzilla.redhat.com/1713371) <b>Attempting to endAction 'RemoveVm' throws ConcurrentModificationException.</b><br>
 - [BZ 1537464](https://bugzilla.redhat.com/1537464) <b>[UI] Unexpected exception: 'b is null' appears in Events window, when using "Host -> Management -> Configure Local Storage" window</b><br>
 - [BZ 1683363](https://bugzilla.redhat.com/1683363) <b>[UI] Long network names cause VM network interface new/edit window to deform</b><br>
 - [BZ 1700413](https://bugzilla.redhat.com/1700413) <b>Rename *Routing Prefix* to *Routing Prefix Length*</b><br>
 - [BZ 1718177](https://bugzilla.redhat.com/1718177) <b>Token based Userinfo API is giving Internal Server Error.</b><br>
 - [BZ 1664338](https://bugzilla.redhat.com/1664338) <b>Live storage migration fails during diskReplicateStart with VolumeDoesNotExist for the new snapshot created on the target domain</b><br>
 - [BZ 1696621](https://bugzilla.redhat.com/1696621) <b>NPE when migrating a VM with missing CPU load</b><br>
 - [BZ 1714587](https://bugzilla.redhat.com/1714587) <b>Able to delete VM snapshot even though rhv console shows image is locked</b><br>
 - [BZ 1688264](https://bugzilla.redhat.com/1688264) <b>[RFE] console.vv: add minimal version for rhel8 virt-viewer</b><br>
 - [BZ 1702230](https://bugzilla.redhat.com/1702230) <b>Converge content type filters in main disk tab</b><br>
 - [BZ 1710818](https://bugzilla.redhat.com/1710818) <b>Connection to host is stucked and host stays NonResponsive until engine restart</b><br>

#### VDSM

 - [BZ 1679478](https://bugzilla.redhat.com/1679478) <b>Use heal info summary to monitor heal</b><br>
 - [BZ 1695037](https://bugzilla.redhat.com/1695037) <b>[SR-IOV] Support 'i40e' driver</b><br>
 - [BZ 1690020](https://bugzilla.redhat.com/1690020) <b>Incorrect I/O when reading and writing OVF disks</b><br>
 - [BZ 1719125](https://bugzilla.redhat.com/1719125) <b>[downstream clone - 4.3.5] lshw can take more than 15 seconds to execute depending on the system</b><br>
 - [BZ 1703132](https://bugzilla.redhat.com/1703132) <b>Prevent ABRT on RHVH nodes "phoning home" (contacting redhat.com) either in all cases or only by explicit approval, never do so by default.</b><br>

#### oVirt Cockpit Plugin

 - [BZ 1727196](https://bugzilla.redhat.com/1727196) <b>Host fail to move to local maintenance from cockpit hosted engine</b><br>
 - [BZ 1721094](https://bugzilla.redhat.com/1721094) <b>Cockpit-ovirt has vulnerabilities in some of its dependencies</b><br>

#### oVirt Hosted Engine Setup

 - [BZ 1715080](https://bugzilla.redhat.com/1715080) <b>Wrong port ":-1" being reported several times, while running "hosted-engine --add-console-password"</b><br>

#### oVirt Ansible hosted-engine setup role

 - [BZ 1698643](https://bugzilla.redhat.com/1698643) <b>can't deploy hosted-engine when eth0 and the default libvirt network try to use the same subnet</b><br>

#### oVirt Log Collector

 - [BZ 1705019](https://bugzilla.redhat.com/1705019) <b>Avoid error when collecting logs on data-centers with no hosts active</b><br>

#### oVirt ISO Uploader

 - [BZ 1722933](https://bugzilla.redhat.com/1722933) <b>ovirt-iso-uploader not parsing ssh login credentials correctly.</b><br>

#### OTOPI

 - [BZ 1723933](https://bugzilla.redhat.com/1723933) <b>systemd services plugin does not support socket units</b><br>

#### oVirt Engine Metrics

 - [BZ 1727064](https://bugzilla.redhat.com/1727064) <b>Deployment from Bastion Machine fails with Ansible 2.8 on upstream</b><br>
 - [BZ 1698888](https://bugzilla.redhat.com/1698888) <b>Update task "Get bastion ssh public key" to use ansible module other then command</b><br>

#### oVirt Engine Data Warehouse

 - [BZ 1673808](https://bugzilla.redhat.com/1673808) <b>ovirt-dwh prevents autovacuum from data garbage collection.</b><br>

#### oVirt Engine UI Extensions

 - [BZ 1717530](https://bugzilla.redhat.com/1717530) <b>[CodeChange][i18n] oVirt 4.3 ui-extensions - revert pt-BR translations</b><br>

#### oVirt Host Dependencies

 - [BZ 1722173](https://bugzilla.redhat.com/1722173) <b>missing iperf3 on RHV-H</b><br>
 - [BZ 1725954](https://bugzilla.redhat.com/1725954) <b>libvirt-admin package not available in RHVH</b><br>

#### imgbased

 - [BZ 1726534](https://bugzilla.redhat.com/1726534) <b>dhclient fails to load libdns-export.so.1102 after upgrade if the user installed library is not persisted on the new layer</b><br>
 - [BZ 1727859](https://bugzilla.redhat.com/1727859) <b>Failed to boot after upgrading a host with a custom kernel</b><br>
 - [BZ 1720310](https://bugzilla.redhat.com/1720310) <b>RHV-H post-installation scripts failing, due to existing tags</b><br>
 - [BZ 1724102](https://bugzilla.redhat.com/1724102) <b>Upgrading the RHV-H will fail if the SELinux is disabled in the server</b><br>

#### oVirt Engine Appliance

 - [BZ 1724076](https://bugzilla.redhat.com/1724076) <b>Failing to build appliance on imagefactory requiring python3 on EL7</b><br>
 - [BZ 1718399](https://bugzilla.redhat.com/1718399) <b>Add yum-utils to ovirt-engine-appliance to unlock disconnected deployments</b><br>

#### oVirt Node NG Image

 - [BZ 1687920](https://bugzilla.redhat.com/1687920) <b>RHVH fails to reinstall if required size is exceeding the available disk space due to anaconda bug</b><br>

### No Doc Update

#### oVirt Engine

 - [BZ 1723794](https://bugzilla.redhat.com/1723794) <b>[downstream clone - 4.3.5] Live Merge hung in the volume deletion phase,  leaving snapshot in a LOCKED state</b><br>
 - [BZ 1716932](https://bugzilla.redhat.com/1716932) <b>NPE Failed to build cloud-init data when initialization object not provided</b><br>

#### Contributors

51 people contributed to this release:

	Ahmad Khiet
	Ales Musil
	Andrej Krejcir
	Asaf Rachmani
	Benny Zlotnik
	Bohdan Iakymets
	Dan Kenigsberg
	Dana Elfassy
	Daniel Erez
	Divan Santana
	Dominik Holler
	Evgeny Slutsky
	Eyal Shenitzky
	Fedor Gavrilov
	Francesco Romani
	Germano Veit Michel
	Gobinda Das
	Greg Sheremeta
	Ido Rosenzwig
	Kaustav Majumder
	Lucia Jelinkova
	Marcin Sobczyk
	Martin Nečas
	Martin Perina
	Michal Skrivanek
	Milan Zamazal
	Mykhailo Kozlovskyy
	Nir Soffer
	Ondra Machacek
	Piotr Kliczewski
	Sahina Bose
	Sandro Bonazzola
	Scott Dickerson
	Scott J Dickerson
	Shani Leviim
	Sharon Gratch
	Shirly Radco
	Shmuel Melamud
	Simone Tiraboschi
	Steven Rosenberg
	Tal Nisan
	Tomasz Baranski
	Tomáš Golembiovský
	Vojtech Juranek
	Vojtech Szocs
	Yedidyah Bar David
	Yuval Turgeman
	bond95
	michalskrivanek
	parthdhanjal
	solacelost
