
..root cause analysis
red hat enterprise linux troubleshooting guide (.pdf 2015)
https://www.redhat.com/en/services/training/rh342-red-hat-enterprise-linux-diagnostics-and-troubleshooting?section=Outline
sysctl
sar

..Experience sizing and rightsizing physical and virtual system resources using
  OS native tools (sar, mpstat, top, vmstat, iostat, etc.)
Don't know. The commands listed are more for auditing or surveying.
df -h
fdisk -l
fdisk /dev/sdb
partprobe /dev/sdb1
pvcreate
vgdisplay
e2fsck -f /dev/vg_sda/lv_sda
resize2fs /dev/vg_sda/lv_sda 1G
lvextend -L+1G /dev/myvg/homevol
vgextend
lvcreate
lvresize
lvreduce --resizefs
lvreduce --resizefs -L 64M vg00/lvol1
vgs

..experience building security controls into new and existing solutions.
There's the STIGs/IAVAs/best practices/exceptions to policy then there's just a
map of who needs what, where, and why. Has more to do with keeping in touch
with changes in personnel (esp. when CIFS config falls out of step with AD,
etc.). The administration is relatively easy as long as you know who needs what,
and under who's authority.

..cfengine

..TCP/UDP network stacks

..strong documentation and written skills

..Centrify (PAM -> Privileged Access Management)
https://www.centrify.com/resources/pam-101/
https://www.centrify.com/support/services/training/
What was the bridge between AD and Red Hat user permissions?
winbindd https://www.samba.org/samba/docs/current/man-html/winbindd.8.html
pam_winbindd.so 
/etc/nsswitch.conf
realm, realm list, realm join
..now apparently part of sssd package
https://www.redhat.com/sysadmin/linux-active-directory
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/windows_integration_guide/sssd-ad
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/windows_integration_guide/sssd-integration-intro#sssd-integration-overview
/etc/sssd/sssd.conf

..strong shell scripting
can, but BASH has too many gotchas and would prefer to just create
utilities (Python, argparse) 

..SELinux
use -Z switch/flag for commands like ls ps
/etc/sysconfig/selinux
'targeted' policy by default
/etc/selinux/config and setting SELINUX=permissive|enforcing|disabled
relabel the filesystem by creating an empty file named .autorelabel
user:role:type:range
system_u:system_r:xserver_t
allow user_t user_home_t:file { create read write unlink };
system-config-selinux (part of policycoreutils-gui)
setenforce Enforcing|Permissive
semanage user|login
chcon
restorecon
genhomedircon
sesearch
setroubleshoot
sealert -b|-a <logfile>
ausearch
auditd
audit2allow

https://wiki.centos.org/HowTos/SELinux

..replicable global solutions against disparate networks, architectures, services 
https://bitbucket-archive.softwareheritage.org/projects/so/sourpoi/minimin.html
https://bitbucket-archive.softwareheritage.org/projects/so/sourpoi/python-openpgp-2440.html
Either some deployment or package manager or good documentation for humans.

..Red Hat Satellite