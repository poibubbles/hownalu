

`/lib/modules/(uname -r)`

```
lsmod  # loaded modules
cat /proc/modules

modinfo <modname>
```
Find out what hardware a module is supporting:
```
lspci -nnk | grep -i 'network\|ethernet' -A3
```
From `lspci` output, what's the difference between:
```
Kernel driver in use: bcma-pci-bridge
Kernel modules: bcma
```



How to find information about the kernel modules installed on the system
https://access.redhat.com/solutions/4246821
