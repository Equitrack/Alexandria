Welcome to my Linux documentation from the EPAM course.

Linux history:

- Development Unix.
- Published as Free BSD by Unix.
- The GNU proyect was started.
- Linux Trovalds developed Linux and integrated with GNU.

Shell:
The shell is an intermediate tool between the user and the operative system that allows interaction with it.

File System:

- Directory structure
- Inodes
- Hard link (link to inode)
- Soft link (link to filename)

Storage:
- LVM

```bash
pvcreate /dev/sdb1
pvscan
pvdisplay
lvgcreate vg_newlvm /dev/sdb1
lvgcreate vg_newlvm /dev/sdb1 /dev/sdc1 /dev/sdc2
lvcreate --name centos7_newvol -l 100%FREE vg_newlvm
mkfs.ext4 /dev/vg_newlvm/centos7_newvol
```
- Swap