
<img width="1566" height="621" alt="image" src="https://github.com/user-attachments/assets/e8077072-c534-4c99-95d0-6d4e7a642659" />

   Runner - is a place where your job gets run, in Jenkins world - it called as agent or worker node, that's where your application gets run on jenkins

GITHUB Actions

1) Self hosted runners -  same concept of what we do in Jenkins,

   In Jenkins, when we take a Jenkins master to execute the workloads,  we would create a Jenkins worker, or jenkins agent - and this can be a EC2 instance or DOCKER container, similarly in GITHUB actions we can do the same thing. 

  
3) Github hosted runners - free for open source or public

When you run a github opensource project - like Kubernetes, ArgoCD, Istio - their CI (Continuous Integration) system is directly built on GITHUB, their source code is also hosted on GITHUB, GITHUB actions using the Github hosted runners is completely free for open source and public projects.

Here in this case  you dont have control over the runners, GITHUB Actions will start a runner, complete the action and then terminates the runner once the action is done.  This is GitHub hosted runner.



# Why do you need a Self Hosted Runners in GITHUB ACTIONS?

we already have a GITHUB Hosted runner, and if it s public project - we are getting it for free, then why do we need a self hosted runner?

Github hosted runners are really good, lot of distributions which are free and can be used for lot of public open source projects, but

If we want to use it for Enterprise company - not open source - i.e. you are using private repositories or even if you are using public repositories where you have lot of configuration where you require huge servers to execute your applications

1) Private project - code is not opensource - nobody can access your github repository
2) Runners that are provided by github are not good enough for your project - if they requried huge RAM like 32GB RAM and large no of CPU's and large processing power, then github provided runners are not enough.

3) Security aspect - if you have a banking application - why would you use a runner which is not in your control.
