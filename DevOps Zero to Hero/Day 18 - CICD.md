# CI/CD

1. Continuous Integration : integrate set of tools or set of processes you follow before delivering your application to the customer
2. Continuous Delivery : deploy your application or deliver your application on a specific platform to your customer



<img width="1114" height="649" alt="image" src="https://github.com/user-attachments/assets/7a166f89-7170-4626-9592-3040eb073604" />


Standard steps you follow before delivering to customer:

1) Unit Testing - testing your code with respect to that specific functionality, this process cannot be manual
2) Static Code Analysis - declaring more variables than using them, lot of memory allocation which is unused
3) Code Quality/Vulnerability testing
4) Automation Testing
5) Reports
6) Deployment - deploying your application to the platorm, where your customer can access.

<img width="1092" height="600" alt="image" src="https://github.com/user-attachments/assets/7f581e2c-c129-4f0e-8580-f0876b33714f" />



<img width="1055" height="591" alt="image" src="https://github.com/user-attachments/assets/02a29fbd-225d-4ac0-bded-d058d0c67b3c" />


<img width="1106" height="676" alt="image" src="https://github.com/user-attachments/assets/41ff7526-d9ed-49e1-b6b8-775e4e4b1ca0" />


<img width="1110" height="662" alt="image" src="https://github.com/user-attachments/assets/586cd535-319d-437d-820e-7508ae9f8c4f" />


<img width="1047" height="617" alt="image" src="https://github.com/user-attachments/assets/f3c46e9f-915a-4174-9578-12071eac1fea" />

<img width="1535" height="897" alt="image" src="https://github.com/user-attachments/assets/e76b32bb-dd53-4c32-a04e-77290b454683" />

Jenkins is not a tool to use, if we want zero master nodes to be started when there is no work load.

We should use - Github actions - which will have kubernetes pods started only when there is need for it, after the work is done all the pods are then deleted.


<img width="1808" height="1022" alt="image" src="https://github.com/user-attachments/assets/2c63d3e1-3c20-4de8-9990-c54046aacc4c" />

Jenkins is event driven - with use of webhooks 

Github actions - is by default event driven














