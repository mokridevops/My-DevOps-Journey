
# Requirement:  
In our organization, As a DevOps engineer I have created lot of EC2 instances, S3 buckets, Lambda functions and lot of user in IAM module.  However, we don't know how much of it are being used by users to the full extent.

For that, we will write a Shell Script by connecting to AWS CLI and get the counts in a file, and try to run the script every day at 6 PM by using a ChronJob.

Usually it is sent to Reporting Dashboard, and then all the managers or respective people will have a look of the utilization of the resources fromt he Reporting Dashboard.

<img width="846" height="637" alt="image" src="https://github.com/user-attachments/assets/228015c4-8af5-4df5-bc36-59646fb770cc" />







