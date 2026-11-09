# Volumes
==========

Containers/Pods are ephemeral.  Data stored inside pod will be deleted once pod is deleted.
EKS cluster is ephemeral including nodes



<img width="732" height="631" alt="image" src="https://github.com/user-attachments/assets/c6dbeda2-9b97-4445-967a-bb7c15ebfc16" />

EBS vs EFS vs S3:
=================
S3 is object storage, we can mount S3 to the instances.  S3 storage is only accessible through HTTP/HTTPS

EBS vs EFS:
===========

1. EBS is like Harddisk, EFS is like MS Drive
2. EBS can only be attached to one instance at a time, EFS can be attached to multiple instances
3. EBS is block store, EFS is file system
   Data is stored as blocks in drives.  Each block is 4kb file size. file systems are responsible to bring the data from disks.
   Filesystems performs CRUD operations on the blocks.
   format disk, create file system and mount to the instance.
4. EFS file system is already decided by AWS as NFS protocol (Network File System). Here we have only step - mount to the instance.
5. EBS is faster than EFS.
6. OS, Database Servers - EBS is the best option, EFS can't work for this, normal files can be stored in EFS.
7. EBS is fixed size, EFS is not fixed, it grows automatically
8. EBS should be in the same availability zone as instance.  EFS can be anywhere in the network.
9. EBS does not need Security Group, EFS requires Security Groups.



Two types of volumes:
1. Ephemeral volumes
2. Permanent volumes

ephemeral volumes:
==================
1. emptyDir
2. hostpath

3. emptyDir is created whenever a pod is created, and deleted when the pod is deleted.
   Containers in the same pod share same network and storage
   
   
