# Jenkins

<img width="1807" height="629" alt="image" src="https://github.com/user-attachments/assets/ac04958f-225c-4173-b622-d235b67f7ddd" />

<img width="1813" height="358" alt="image" src="https://github.com/user-attachments/assets/db6768bd-f2ec-4561-ab29-453bf2924f44" />

<img width="1738" height="164" alt="image" src="https://github.com/user-attachments/assets/5ea52b05-4199-4d3c-be8f-d744d36ade58" />



<img width="1096" height="703" alt="image" src="https://github.com/user-attachments/assets/3a3fd04a-8bb0-4a9a-845d-97fdcca3f01a" />


Jenkinsfile

pipeline {
   agent any

   stages {
      stage('Build') {
        steps {
         echo 'Building...'
      }
     } 
      stage ('Test') {
        steps {
         echo 'Testing...'
      }
     }
      stage ('Deploy') {
        steps {
         echo 'Deploying...'
         }
      }
    }
 }    


 To view stages in the pipeline -> we need to install -> pipeline stage view plugin

 <img width="1739" height="928" alt="image" src="https://github.com/user-attachments/assets/c39a1da7-0bdc-4d74-8e82-1157504eeca2" />

 <img width="1620" height="984" alt="image" src="https://github.com/user-attachments/assets/a13c5082-0267-4c36-8806-3b9146305391" />

 <img width="920" height="941" alt="image" src="https://github.com/user-attachments/assets/ddca7158-84d5-4b33-9ac7-d825d7db96b2" />

 <img width="671" height="732" alt="image" src="https://github.com/user-attachments/assets/1de0fd87-85dd-472f-8928-80b8cbcecaac" />

<img width="664" height="683" alt="image" src="https://github.com/user-attachments/assets/caec1716-01c4-4862-a786-8588e725f7e8" />


<img width="1423" height="945" alt="image" src="https://github.com/user-attachments/assets/d07a96c0-75ab-4403-97d4-60a613daa2b7" />

it takes the jenkins file from the git repo that you mentioned in the pipepline scm location - and it will start execution


<img width="902" height="864" alt="image" src="https://github.com/user-attachments/assets/01689942-8825-4418-b29c-ffa9818a0305" />

we don't see any pipeline execution - dashboard kind of stuff here, hence we install a plugin called => pipeline stage view plugin

<img width="1902" height="677" alt="image" src="https://github.com/user-attachments/assets/f742d8b5-a592-49cb-84e2-fb75d1f6c25b" />

once we install that plugin - we see the tabular view of the pipelines:

<img width="1221" height="843" alt="image" src="https://github.com/user-attachments/assets/bd8a692a-4e8e-4d85-b02a-b7d0fc235278" />

the above pipeline is called as Declarative pipeline.

Two types of pipelines:
=======================
1. Declarative
2. Scripted
   
advantages of pipeline:
version control, review the changes through PR, restore, reuse, etc

<img width="1807" height="298" alt="image" src="https://github.com/user-attachments/assets/0cb3afdb-762d-4ea6-bf22-0b0b153faf78" />

we use hybrid pipeline approach - combining declarative and scripted pipeline:

pipeline {
  agent any

  stages{
    stage('Build') {
      steps {
         script {
         sh """
           echo "Building"
           """
           }
      }
    }
    stage('Deploy') {
     steps {
       script {
          sh """
            echo "Deploying"
            """
       }
     }
  }
    stage('Test') {
     steps {
       script {
         sh """
            echo "Testing"
            """
         }
     }
     }
  }
} 


The above is hybrid pipeline


Jenkins Master Node architecture:
=================================
Master node can't take the builds, it can just get the trigger and assign node to run the build.
We can have multiple nodes based on different configurations, separate nodes for java projects, nodejs projects, python projects, ios projects, android etc...

Master -> will monitor the nodes, collect the logs, etc

<img width="1132" height="467" alt="image" src="https://github.com/user-attachments/assets/c7b4a338-5bfe-4bf8-9de4-8d1ac1d26603" />


<img width="1045" height="938" alt="image" src="https://github.com/user-attachments/assets/135f4a5a-c5ef-4e7d-9890-e2344edfbe7a" />

got the code from bastion server setup - when we added extra disk space:

<img width="1676" height="1006" alt="image" src="https://github.com/user-attachments/assets/56a62bcc-2003-428d-a5be-f2c8113aebab" />

<img width="905" height="256" alt="image" src="https://github.com/user-attachments/assets/e65cbe15-16c8-4309-965d-ac70e6ffb1ad" />

<img width="1164" height="418" alt="image" src="https://github.com/user-attachments/assets/e13e713f-1af0-4760-9447-f14477d6b522" />


we need to install java in jenkins agent also:

<img width="1710" height="398" alt="image" src="https://github.com/user-attachments/assets/e9903c52-02db-419c-9b58-c3643676ccba" />


<img width="1648" height="257" alt="image" src="https://github.com/user-attachments/assets/d46ca4b2-3b6a-4490-b00c-1847d1447742" />


<img width="1632" height="587" alt="image" src="https://github.com/user-attachments/assets/af5215fd-082b-4fdf-8dad-ac27be1f69a1" />

after installing java in the agent node:

we need to add an agent in jenkins console:


<img width="1889" height="942" alt="image" src="https://github.com/user-attachments/assets/5e65bd36-33bc-4725-bb72-62e1993801ba" />
<img width="1867" height="639" alt="image" src="https://github.com/user-attachments/assets/0b654941-805c-4f41-b676-a7de13eb21d8" />

we should never allow Jenkins master to run the jobs, we should give it to nodes:

<img width="1215" height="666" alt="image" src="https://github.com/user-attachments/assets/42366998-ff5c-4a1b-aec0-90a6f0b45abb" />

<img width="1222" height="686" alt="image" src="https://github.com/user-attachments/assets/4c46783f-6783-4bc2-b468-e8056250f51c" />

<img width="1740" height="848" alt="image" src="https://github.com/user-attachments/assets/034a965f-2aac-498f-8ad9-9028495d2644" />

<img width="1461" height="579" alt="image" src="https://github.com/user-attachments/assets/16963a74-d7f4-473e-ad6e-f2d6dad62b49" />

<img width="1655" height="709" alt="image" src="https://github.com/user-attachments/assets/422b669a-0e86-4440-b8a3-581dbc0d069c" />

<img width="1664" height="619" alt="image" src="https://github.com/user-attachments/assets/14aa1de3-fc6e-4659-a41d-de630a0efe24" />


<img width="1674" height="754" alt="image" src="https://github.com/user-attachments/assets/23e1e6d1-3eb2-49dd-ba68-e23bd386f8db" />


<img width="1751" height="965" alt="image" src="https://github.com/user-attachments/assets/40a64f80-dc49-4ddb-9624-fd775b2f0ad8" />

<img width="1706" height="859" alt="image" src="https://github.com/user-attachments/assets/bc2e516c-5d56-41f0-8c6e-6baad6253528" />

<img width="1721" height="679" alt="image" src="https://github.com/user-attachments/assets/92aa2dd2-c8a3-4cda-bb51-9fbdf35c0244" />



<img width="1738" height="845" alt="image" src="https://github.com/user-attachments/assets/ee69767a-a802-4113-bc91-42c4849dcd92" />


<img width="1890" height="655" alt="image" src="https://github.com/user-attachments/assets/7fbb8070-2fe7-48fd-ae08-76adfe325575" />

<img width="1547" height="1035" alt="image" src="https://github.com/user-attachments/assets/1b83cb5d-6597-4a25-bb4c-8c9a2b657640" />


<img width="1404" height="984" alt="image" src="https://github.com/user-attachments/assets/1c1408fb-c886-4b38-a68e-c621683e2944" />


Now, master will see this agent in the Jenkinsfile code, 

<img width="415" height="180" alt="image" src="https://github.com/user-attachments/assets/97e60974-3fb8-4fd3-b3fa-a56c4a762a85" />

and see that they are selecting node label as : ROBOSHOP, hence it will execute this pipeline in this agent which has name as: ROBOSHOP

<img width="1541" height="965" alt="image" src="https://github.com/user-attachments/assets/4128106c-6b57-4629-840c-a7b1a63823a6" />

<img width="1129" height="925" alt="image" src="https://github.com/user-attachments/assets/bec79bfe-25d8-4fb5-a4f2-a6afc41f1d6a" />


<img width="1362" height="717" alt="image" src="https://github.com/user-attachments/assets/911e7eff-9897-4ff9-993b-f0cb2c049f16" />

<img width="1358" height="907" alt="image" src="https://github.com/user-attachments/assets/5bbc9936-0f1b-4bcf-b8de-0c04858d4cd9" />



<img width="1760" height="1012" alt="image" src="https://github.com/user-attachments/assets/c48285b2-d2bf-4360-a5c8-b3c5d710e6ce" />


<img width="1604" height="955" alt="image" src="https://github.com/user-attachments/assets/f84e2525-9696-48c5-b66f-2dce281342d8" />

<img width="1810" height="1003" alt="image" src="https://github.com/user-attachments/assets/f0a781fa-30da-4308-8e97-bf81169e8241" />

<img width="1719" height="996" alt="image" src="https://github.com/user-attachments/assets/531602c8-0a61-4365-92c2-a2e46793ab40" />

if DEPLOY == true, then this will execute, else it will no exectue

<img width="1322" height="917" alt="image" src="https://github.com/user-attachments/assets/72518f59-4708-414a-9b0e-fe7460dd4b6f" />

unselecting DEPLOY:

<img width="1790" height="962" alt="image" src="https://github.com/user-attachments/assets/891fc93c-8746-41cf-b7ff-64514296a78d" />

<img width="1382" height="956" alt="image" src="https://github.com/user-attachments/assets/ad6f6a99-fea8-4cc5-9e6c-24b1a9673686" />



<img width="1119" height="989" alt="image" src="https://github.com/user-attachments/assets/57761f27-82b4-47eb-8027-f4ec61584551" />




