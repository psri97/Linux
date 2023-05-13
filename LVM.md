### LVM (Logical Volume Manager):
    - Logical Volume Management or LVM is a framework of the Linux operating system that has been introduced for the easier management of physical storage devices. 
    - The concept of logical volume management is very much similar to the concept of virtualization
    Advantages of LVM:
    - It allows you to efficiently manage and utilize your physical disk space.
    - It is capable of creating such logical volumes whose capacity can be increased or decreased depending upon your requirements.
    - If you intend to keep backups of your data on multiple logical volumes, then this increases the availability of your data.
    - A new physical device can easily be added below the volume group with zero downtime and without any service disruption.
    - LVM allows you to partition a single physical device into multiple logical partitions as well as it also allows you to integrate multiple physical devices into a single volume group.

## commands to practice LVM on linux machines
    Lets add two or multiple disks to instance
- Check whether it is added disks to instance or not using command:
    lsblk 
- Now, we can create physical volumes using command:
    pvcreate /dev/xvdf
- Then we can check the created physical volumes using command:
    pvdisplay
- Then have to create volume group for physical volumes using command:
    vgcreate /volumegroup1 /dev/xvdf /dev/xvdg
- Then we can check the created volume group using the command:
    vgdisplay
- Now, we can create logical volues using the command:
    lvcreate -L 2G -n awslv01 volumegroup1
- Then we can check the created logical volumes using the command:
    lvdisplay
- After that we have to make it a filesystem using a command:
    mkfs.ext4 /dev/volumegroup1/awslv01
- Then have to create directories using command:
    mkdir awslvm01
- Then have to mount using the command:
    mount /dev/volumegroup1/awslv01 awslvm01
- Have to check the mounting points using a command:
    df -h
- then have to extend the logical volume using the command:
    lvextend -L +2G /dev/mapper/volumegroup1-awslv01
- After extending the lv we have to resize it using the command:
    resize 2fs /dev/mapper/volumegroup1-awslv01
- Alternative approach for extending volume using below instructions:
    1. without creating filesystem volume cannot be used so first create a filesystem using mkfs.ext4 /dev/mapper/volumegroup1-awslv01
    2. we cannot create a filesystem when it is mounted on the linux machine at this point. we have to umount and mount again after creating file system on the extended volume.
- vgextend <VG-Name> </dev/xvdg> - volumegroup size will be extended.
- vgremove <VG-Name> - VolumeGroup can be deleted
- lvremove </dev/vg1/lvm01> - Logical Volume will be removed
- pvremove </dev/disk1> </dev/disk2> <> physical volumes will be removed