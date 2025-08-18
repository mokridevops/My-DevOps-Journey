
# Day to Day activities of a DevOps Engineer

1) Every three months - new version of ios, android, these will create new fixes to be done in the program by the developers, which will create work for infrastructure, and also might require configuration changes to the infrastructureNe and devops engineers need to stay up to date on these.
2) New microservices getting added to the project - they as a devops engineer - you have to setup the infrastructure requirements for it, and write the CICD pipelines, might have to look into kubernetes cluster configuration for these microservices

3) As a devops engineer - you might have to continuously maintain your existing pipelines, or upgrade your kubernetes clusters,

   10 - 15 kubernetes clusters in your organization - you might have to upgrade continously to new version, when there are patches or vulnerablities or CDE's, you can move to automatic updates by the cloud providers or manage them by yourself

   4) Migration activities of suppose lets say - ansible shell scripts to gitops architecture, you will first do a POC with one microservice and see if it is working fine, then you will migrate 10 microservices at a time, and then do next 10 ...etc, this is an ongoing activity, not one day activity
  
   5) On premise to cloud migration - which take years to migrate
   6) Cost Optimization - for each of the AWS services, you have to do cost optimization - suppose you do the cost optimization for S3 buckets now, later you might have to do cost optimization for other services like EBS, EFS
   7) Security and Compliance - Security patches
   8) feature enhancements for CICD pipelines - moving from Jenkins to GitHub Actions, or within GitHub Actions, you want to move out of certain plugin and implement a new plugin
   9) Handle lot of tickets from Development teams
   
