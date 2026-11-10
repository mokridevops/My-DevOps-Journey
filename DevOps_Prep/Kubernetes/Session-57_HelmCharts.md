# Helm Charts #
1. Build the image -> open source nginx, mongo, node, etc
2. Run the image -> manifest files
   
Two advantages of Helm Charts:
1. package manager
2. templatize manifest files -> keep place holdes, submit values at runtime


   <img width="1677" height="804" alt="image" src="https://github.com/user-attachments/assets/21d48850-05ae-49b0-9db8-1247960dc02e" />

<img width="820" height="454" alt="image" src="https://github.com/user-attachments/assets/7e44ecb9-4a03-42c4-bcf2-bcf9ecf08cdc" />


<img width="1093" height="958" alt="image" src="https://github.com/user-attachments/assets/e8874fec-fb3a-4500-a0d1-a2d8655d703f" />

<img width="1881" height="817" alt="image" src="https://github.com/user-attachments/assets/07bb0293-6104-463c-b3b3-c7bea06ade6f" />

<img width="1052" height="1026" alt="image" src="https://github.com/user-attachments/assets/556a1ff0-8077-49ff-a77a-022a157533b8" />

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
  # labels related to deployment resource
  labels:
    project: roboshop
    tier: frontend
    component: frontend
    purpose: deployment
spec:
  replicas: {{ .Values.deployment.replicas }}
  selector:
    matchLabels:
      project: roboshop
      tier: frontend
      component: frontend
      purpose: deployment
  # Pod
  template:
    metadata:
      labels:
        project: roboshop
        tier: frontend
        component: frontend
        purpose: deployment
    spec:
      containers:
      - name: nginx
        image: nginx:{{ .Values.deployment.imageVersion }}
        ports:
        - containerPort: 80


        ----------------------
        <img width="1427" height="1028" alt="image" src="https://github.com/user-attachments/assets/7f1131bd-8af7-408c-8a9b-7ef4147e2327" />

---
apiVersion: v1
kind: Service
metadata:
  name: nginx
  # servicer labels
  labels:
    project: roboshop
    tier: frontend
    component: frontend
    purpose: deployment
spec:
  # Service uses the below labels to select the pods
  type: {{ .Values.service.type }}
  selector:
    project: roboshop
    tier: frontend
    component: frontend
    purpose: deployment
  ports:
    - protocol: TCP
      port: 80 # service port
      targetPort: 80 # container port


      -------------------
      <img width="1379" height="847" alt="image" src="https://github.com/user-attachments/assets/9e4bb3a3-4c78-4442-9615-8a7e2cc372b9" />

<img width="761" height="448" alt="image" src="https://github.com/user-attachments/assets/1b685c8e-45bf-4c1d-bf9d-c878b800ec6d" />

<img width="774" height="544" alt="image" src="https://github.com/user-attachments/assets/e40c5293-be98-4ede-bb3f-0c2f47215bc4" />

<img width="797" height="647" alt="image" src="https://github.com/user-attachments/assets/e073eff3-ff3d-4737-8c38-73ebc636f1e9" />

<img width="698" height="691" alt="image" src="https://github.com/user-attachments/assets/a13e69e0-0462-4672-89ac-d81336d5247b" />


all common values - we place in values.yaml
dev env related values - we place in values-dev.yaml
prod env related values - we place in values-prod.yaml

<img width="1733" height="813" alt="image" src="https://github.com/user-attachments/assets/0ef48bff-6404-477c-bc57-af6d91d256d0" />



We will keep environment specific values separate, we will apply/upgrade chart with those values at run time. Image is same across all the environments, only values means configuration changes.

Chart.yaml -> contains all the chart related configuration like name, chartversion, apiversion, description, etc.
templates -> where we keep all the manifest files with placeholders
values.yaml -> we maintain default values for the templates placeholders

<img width="1118" height="654" alt="image" src="https://github.com/user-attachments/assets/450ff9b4-318a-42c9-97cd-42c153a57c2f" />

we substitute the place holders with actual values.







      
