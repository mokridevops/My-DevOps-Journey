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
   Containers in the same pod share same network and storage.  emptyDir is used to share the storage between containers in the pod.  A usecase is - we use emptyDir to ship pod logs to ELK.
   
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


daemonset:
==========
Kubernetes makes sure of running one pod replica in each and everynode.  this pod is used to collect host metrics, logs, etc...using hostPath

hostPath is administrator activity...
1. namespace level ->
2. custer level -> admin...


   <img width="1485" height="979" alt="image" src="https://github.com/user-attachments/assets/493e1508-f83a-4788-abcb-8edb5ad79739" />
   <img width="1456" height="867" alt="image" src="https://github.com/user-attachments/assets/10916251-0bfe-4169-b8ec-896bfa54ae97" />

   <img width="1273" height="927" alt="image" src="https://github.com/user-attachments/assets/2bf9363a-0f61-4ef9-b29f-7be3ef885758" />

   if you notice, two replicas are created


   Storage admins
   ==============
   1. keep the data secure
   2. daily backups are mandatory
   3. restore
   4. restore testing (before a crash)
   5. archieval - old data
   6. replicate - atleast in 3 disks

   if on-premise manual cluster:
   ----------------------------
   1. raise a ticket, take approval from team lead/manager
   2. assign this ticket to storage team... mention how much disk you want, with reasons, etc..
   3. storage team lead approves. member creates storage and gives the address to us.
   4. send an email to admin team.


<img width="614" height="345" alt="image" src="https://github.com/user-attachments/assets/c711224b-4d85-4e8a-a9ec-f0f0e8cc1a84" />

K8-admin and storage-admin are two different roles, K8-admins doesnot really know about storage, and Storage-admins doesnot really know about K8s.

Hence, Kubernetes created - some wrapper objects on top of storage objects...

PV - Persistant Volume
PVC - PersistantVolumeClaim
SC - StorageClass

<img width="1185" height="696" alt="image" src="https://github.com/user-attachments/assets/46090f83-a98d-416b-809a-f67ae3bc13fb" />

PV
===
PV is equivalent logical K8 resource of underlying disk...
It is the physical representation of the disk.

the disk itself is becoming PV in Kubernetes, like a reference point for the disk


in EBS, there are two types of provisioning:
1. static provisioning -> we create disk manually and mount it
2. dynamic provisioning -> K8 will create disk automatically

EBS Static:
==========
1. Install EBS drivers
   EBS CSI Drivers:
   <img width="926" height="488" alt="image" src="https://github.com/user-attachments/assets/b5dc4411-6cb6-4410-8379-c07cda98b5f3" />
kubectl apply -k "github.com/kubernetes-sigs/aws-ebs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-1.67"
<img width="844" height="242" alt="image" src="https://github.com/user-attachments/assets/f77efd31-4cfd-460c-8949-e62d50b2a003" />

it installs drivers.

After installing drivers, you need to give permission to EKS nodes
<img width="780" height="236" alt="image" src="https://github.com/user-attachments/assets/67cb9a24-9b07-4028-ba5d-694881731e8a" />

<img width="944" height="521" alt="image" src="https://github.com/user-attachments/assets/1a0ee3bb-47dc-42e3-89cc-379036fa787f" />

<img width="949" height="526" alt="image" src="https://github.com/user-attachments/assets/f5b073d5-a059-4042-8c83-160079f5dc36" />
<img width="947" height="508" alt="image" src="https://github.com/user-attachments/assets/69740f93-af87-4f5e-a7c3-b901f374a29d" />

<img width="953" height="494" alt="image" src="https://github.com/user-attachments/assets/fb53410b-1c66-470e-87f2-091cd420a9f3" />

this policy is about mounting the volumes
<img width="935" height="505" alt="image" src="https://github.com/user-attachments/assets/bb596e80-f753-4637-b8cf-b5b56a4c94cc" />
<img width="755" height="377" alt="image" src="https://github.com/user-attachments/assets/b5ec1aa1-9fa1-4080-b76b-c6e45fc90f3e" />


3. EKS nodes should have access to mount EBS disks.
4. Create the disk, where the EKS node is available.

   we have our instances in 1b and id:

   <img width="791" height="206" alt="image" src="https://github.com/user-attachments/assets/2a9f8692-8c41-4cc4-80f8-12854042822a" />

   

6. Create PV

lets create the disk in 1d,

<img width="656" height="466" alt="image" src="https://github.com/user-attachments/assets/e15510ed-3746-4368-8d8a-6c781778023a" />


<img width="947" height="471" alt="image" src="https://github.com/user-attachments/assets/1e477510-eed0-411a-b5e7-a2169cc91e7a" />

vol-08d48552c12f0bae2

now, creating PV for the above EBS disk created for 2 GB:

<img width="773" height="446" alt="image" src="https://github.com/user-attachments/assets/689b9beb-e57f-458f-9964-a0f9cf6bf378" />

<img width="872" height="493" alt="image" src="https://github.com/user-attachments/assets/ad3c8849-7fb5-4ce0-a445-2474a3309153" />

<img width="629" height="460" alt="image" src="https://github.com/user-attachments/assets/63da2bdb-8cc9-4622-9984-6772af2b35f2" />

we need to give the same 2 GB, and also list the Volume Handle: the volume name that we got earlier, while creating volumes



<img width="629" height="460" alt="image" src="https://github.com/user-attachments/assets/224be068-94fd-402a-9e88-b22f7598155c" />

accessmodes
===========

<img width="629" height="460" alt="image" src="https://github.com/user-attachments/assets/2fea788e-0ef5-45bb-a9d1-68b8cbc9f0b6" />


 1.   readWriteOnce -> at a time only one node can access. pods in that node can access
 2.   ReadOnlyMany -> at a time multiple nodes can readOnly.
 3.   ReadWriteMany -> at a time multiple nodes can read and write.
 4.   ReadWriteOncePod > only one pod can read and write.

    
    
    <img width="561" height="260" alt="image" src="https://github.com/user-attachments/assets/dad4899e-75bb-472a-97ed-49387d8612ed" />

<img width="668" height="239" alt="image" src="https://github.com/user-attachments/assets/fdeb7f0b-c072-4550-9585-fa687ad61244" />

<img width="668" height="239" alt="image" src="https://github.com/user-attachments/assets/2a616271-bcd5-4907-ad71-eff73527696c" />

RWO - ReadWriteOnce

Reclaim policy -> 
---------------
1. delete -> automatically removes both the PV object from kubernetes and the actual storage
2. Retain -> data will be persisted even when PV and Pod are deleted
3. Recycle -> data will be erased, but disk will be there.


PVC: logical representation - i.e. it claims this disk space for pod
====
now disk is created, and PV is also bound to that disk...
PVC is claim against PV to use the storage disk

<img width="1141" height="588" alt="image" src="https://github.com/user-attachments/assets/f60bf4da-d8cc-4487-a13a-13143aecd61d" />

son -> mother -> father -> wallet
POD    PVC        PV       Storage


<img width="1882" height="811" alt="image" src="https://github.com/user-attachments/assets/a3b9b3b2-73d7-4f77-9100-73d529804897" />


<img width="1471" height="933" alt="image" src="https://github.com/user-attachments/assets/f4a686b7-9a17-49da-8c44-39851aa4c06e" />

<img width="1699" height="931" alt="image" src="https://github.com/user-attachments/assets/93d3afb0-d2b7-4676-8537-b0139de7e9e5" />

now, lets give this PVC to POD:



<img width="932" height="391" alt="image" src="https://github.com/user-attachments/assets/9fd3cdb1-5926-40d9-a3de-448d8ad0da60" />


<img width="700" height="485" alt="image" src="https://github.com/user-attachments/assets/3a38139d-5f00-4dc1-be1a-1561a0c1a59a" />

<img width="805" height="456" alt="image" src="https://github.com/user-attachments/assets/5f8463dc-64e9-48e3-a6bc-e6bedefcdfff" />


<img width="767" height="425" alt="image" src="https://github.com/user-attachments/assets/8645b1b4-b161-452e-a06b-112d99389911" />

<img width="655" height="398" alt="image" src="https://github.com/user-attachments/assets/5824d117-5e60-4ee6-89fe-acdd969981ce" />

to describe a pod:
> kubectl describe pod ebs-static

I entered into the pod and created the index.html file

<img width="624" height="385" alt="image" src="https://github.com/user-attachments/assets/1aae9b6a-033b-446c-ab68-14d5d1c4af7c" />


now, I will delete the pod, and create another pod, and want to check if the data is still there or deleted?

<img width="525" height="213" alt="image" src="https://github.com/user-attachments/assets/befe3039-06d9-4e51-bc2d-85c266e5932b" />

<img width="948" height="287" alt="image" src="https://github.com/user-attachments/assets/79e43e96-4917-4e9c-b2d4-fe26adcb0aef" />

that volume became available now

now lets create the pod again

<img width="540" height="193" alt="image" src="https://github.com/user-attachments/assets/8aed9967-f0f1-4dcd-b43e-f0458f86019d" />

<img width="522" height="152" alt="image" src="https://github.com/user-attachments/assets/c3131cf3-7026-4b89-ad07-a0aa059dc6ea" />

<img width="356" height="455" alt="image" src="https://github.com/user-attachments/assets/a1cce98b-7c99-4ee2-a56b-0f791ff23998" />

you can see index.html is still available here, it did not disappear when pod is deleted, so this is persistent volume


now, due to our luck kubenetes is sending the yaml file that we are running in to zone 1d, it can go to zone 1b too, if it goes to zone 1b, then our volume will be in a different zone, hence it will not mount.

for this - the is a facility in kubernetes to select the node - called -> node selector

Scheduler:
----------
responsible to schedule the pods in the nodes, it uses different considrations to select the node.  We can control this.


<img width="834" height="188" alt="image" src="https://github.com/user-attachments/assets/87d17a96-8991-4bf5-9dbf-140ec6661828" />

<img width="881" height="460" alt="image" src="https://github.com/user-attachments/assets/6c5c4cbb-1d8d-4544-9823-2c673ad7e8a8" />

we are telling kubernetes to send the pod to the node which is in us-east-1b












