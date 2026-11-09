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

   emptyDir is created whenever a pod is created, and deleted when the pod is deleted.
   Containers in the same pod share same network and storage.  We use emptyDir to ship pod logs to ELK.
   
   Volumes -> Pod level
   VolumeMounts -> We need to mount to volume to individual container.

<img width="1647" height="834" alt="image" src="https://github.com/user-attachments/assets/91fabd7e-de8b-44e9-985d-5c3228f4f748" />

we are mounting the volumes -> nginx-logs to the containers -> nginx and nginx-logs
<img width="1017" height="490" alt="image" src="https://github.com/user-attachments/assets/fe82e7d7-9b7d-4f2a-89f3-d0f09f823607" />

<img width="1126" height="448" alt="image" src="https://github.com/user-attachments/assets/00e69e96-9200-4508-a482-cdf7f8dcd2c9" />

we see that almalinux is able to access these logs

<img width="1191" height="654" alt="image" src="https://github.com/user-attachments/assets/1d47c7f4-ed07-4748-9f6b-06f7c63fadfd" />



<img width="802" height="385" alt="image" src="https://github.com/user-attachments/assets/9aac504c-6bb2-43b9-a653-8863acdd6814" />

### *** We create emptyDir -> to shift the pod logs from pod to ELK***

hostPath
========
if you store pod data in the host, when pod is deleted and recreated, it can be scheduled in any other node, however pod can't mount data in other node.

hostPath is used to ship the host logs outside of Kubernetes like ELK (Elastic Log Stash Kibana) - this is sever that hosts the logs.  We mount hostPath to containers and allow the containers to ship the logs to ELK.

hostPath is not secured, we use in rare cases like shipping host logs to ELk, here we can take a precaution of <B>readonly true..</b>

Note: we should store the pod related logs in hostPath, we should use hostPath to ship the logs to ELK.








   
