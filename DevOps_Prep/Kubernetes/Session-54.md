
Session 54:
===========

EBS Static:
===========
1. Need to add EBS drivers
2. IAM EBSCSIDriverPolicy to Worker nodes
3. Created disk
4. Create PV
5. Create PVC
6. add volume in pod

EBS Dynamic:
============
StorageClass -> used to create storage and respective PV automatically
for example, we create one storageClass for EBS, one storageClass for EFS 

1. Need to add EBS drivers
2. IAM EBSSCIDriverPolicy to worker nodes
3. create storage class


Retain: Data and disk will be persisted
Recycle: data will be deleted disk will be persisted
Delete: data and disk will be deleted


emptyDir.yaml
-------------
apiVersion: v1
kind: Pod
metadata: 
 name: nginx
spec: 
  containers: 
  - image: nginx
    name: nginx
  - image: almalinux:9
    name: almalinux
    command: ["sleep","1000"]


    ----------------------

    Storage class:

    apiVersion: storage.k8s.io/v1
    kind: StorageClass
    metadata:
      name: roboshop-ebs
    provisioner: ebs.csi.aws.com
    reclaimPolicy: Retain
    volumeBindingMode: WaitForFirstConsumer
    
