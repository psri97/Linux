Linux Commands
PWD -- It is used to print the Present writing directory
ls -- It is used to show the list of files
ls -la -- It is used to show along with list of hidden directories and files
touch -- It is used to creates a empty file
cat -- it is used read the content of the file
echo -- it is used to print whatever we provide it as input
vi -- it is a editor where we can edit the files and save the files using it
mkdir -- it is used to create an directory
rmdir -- it is used to delete directory
mv -- it is used to move a file or directory for one location to another location or else we can use it for changing the name of file or directory
ls -lrt -- it is used to list the files with time stamp
:wq! -- it is used to save the data and quit from vi editor
INSERT -- to enter any data the editor should be in insert mode
ESC -- it is used to perform operations like knowing number of lines in the file
:set nu -- it is used to Know the number of lines in a file
rm -- it is used to remove or delete the file



--------------------------------------------------------------------------------------------
How to Perform Disk Partitions
-- find out list of block devices (disks and mount points) using a command: lsblk
-- format a newly attached disk using the command: fdisk 
    lets assume the attached new disk is xvdf (20gb)
    follow the steps
    fdisk /dev/xvdf
    select the command m for help to partition accordingly
-- Creating file system for the partitioned disk using command: mkfs.ext4 /dev/xvdf1
-- mounting the partition disk to /Folder1 using command : mount /dev/xvdf1 /Folder1     
note: if we use mount command to mount tha disks then it is creating a temporary mount point. it is not recomended because if the server restarts then the mount points will be removed. 
we should always save the mount points in /etc/fstab then it will create a permanent mount point 
