
## Session 53:

<img width="1813" height="844" alt="image" src="https://github.com/user-attachments/assets/c6dc7e17-3c63-48b2-993b-d4c55dcf5d0f" />


nodePort: if you hit any worker node with the nodePort open, traffic will be forwarded to clusterIP and then to the pod

Pods will be registered as endpoint for the service


Sets:

 1. replicaset
 2. deployment
 3. statefulset
 4. daemonset

replicaset - it makes sure desired number of replicas running all the time.  it will use labels to match, labels are used as selectors within kubernetes resources

deployment - deployment creates replicaset, replicaset creates pods.
deployment is -> removing the old image pods and creating the new image pods by using the strategy called as Rolling Update, by which we don't have any down time.

<img width="1005" height="654" alt="image" src="https://github.com/user-attachments/assets/f3b5cb5b-b5df-49d1-908d-752b47579174" />

<img width="1251" height="594" alt="image" src="https://github.com/user-attachments/assets/7116c83a-b2de-4b40-ae57-c042b14ec8e7" />

configMap:
==========
Key value pairs application configuration

but we can keep files also in configMap

nginx.conf is key, value is nginx.conf file content

if nginx.conf changes?

we need to rebuild the image with new version, push the image and change the manifest image version


envFrom:
- configMapRef:
     name: fronend-config

  we need to mount the config file as volume to the pod

  docker:
  =======

  volumes:
  - mongodb
 
  volumeMounts:
  - mongodb:/data/db


 <img width="1300" height="195" alt="image" src="https://github.com/user-attachments/assets/2ee1c62c-6188-46db-baaa-8495002311db" />

 <img width="387" height="190" alt="image" src="https://github.com/user-attachments/assets/5d20eb98-887b-4f36-a01c-d9b4a1dfa6c2" />

 <img width="1800" height="180" alt="image" src="https://github.com/user-attachments/assets/8339fc24-83a0-44b7-9689-3acb22d24931" />

 this is called self healing (liveness probe)


<img width="824" height="511" alt="image" src="https://github.com/user-attachments/assets/1b03577f-7cc8-4cdc-8924-5acada690995" />





  


