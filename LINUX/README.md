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
- Inodes (metadata of files)
- Hard link (link to inode)
- Soft link (link to filename)

Storage:
- LVM

```bash

# CREATE PHYSICAL VOLUMEN
pvcreate /dev/sdb1

# SHOW INFO
pvdisplay

# CREATE 
lvgcreate vg_data /dev/sdb1
lvcreate -n lv_docs -L 20G vg_data

# EXTEND
vgextend vg_data /dev/sdb2
lvextend -L +10G /dev/vg_data/lv_nombre

# FOTRMAT
mkfs.ext4 /dev/vg_data/lv_nombre\

# PERSITENT VOLUME
tail -n 1 /mnt/fstab > /etc/fstab

# RESIZE

resize2fs /dev/vg_nombre/lv_nombre #EXT4
xfs_growfs /mnt/punto_montaje #XFS
```
- Swap
```bash
# CHECK
cat /proc/swaps
free -h
```