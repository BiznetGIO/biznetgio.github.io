We define 2 stage deploy project to public, staging and production. 
Staging is internal release, this phase process to test and review by product owner. 
After apps ready successfully runnning on staging, all feature will be check according with product documentations.
This step make sure of all functional feature works normally before move to productions.

## Staging Phase
Autodevops deployment staging process by pipeline gitlab ci/cd .
Pipeline are the top-level component of continuous integration, delivery, and deployment.
Pipeline comprise with jobs and stage. Job define _what_ process todo, and stage define _when_ process to do. 

In our Staging, we determine 4 step stage. 

- Test
- Build
- Release
- Deploy
 
<p align="center">
	<img src="../img/pipeline-giov2api-staging.png">
</p>

If either one or some stage fail, another next stage can not be proceed and the pipeline ends early.

Some conditions on fail, you can retry a stage to rerun jobs execute again. 
To monitoring jobs execute, detailed can be view as linux terminal(tty) on browser.    

### 1. test 
Test stage is doing jobs verify with internal test package and sonarqube. Common project microservice/backend python include with testing code, pytest or unittest to testing functional and libraries. By default test stage will send project to sonarqube, output can be viewed on our [sonarqube site](https://cq.biznetgio.dev/). 
<p align="center">
	<img src="../img/pipeline-giov2api-test.png">
</p>


### 2. build
Build stage is step when containerize the applications. Jobs build container image base on `Dockerfile` that include on your project folder. 
<p align="center">
	<img src="../img/pipeline-giov2api-build.png">
</p>


### 3. release
Release stage is step push/upload successfull container image to our registry image. 
This step register an image container with tag `latest` and ready to deploy on staging server. 
<p align="center">
	<img src="../img/pipeline-giov2api-release.png">
</p>


### 4. deploy
This final step to running your containerize applications on staging server. 
It will automatically detect `orcinus.yml` on container production enviroment and up onto staging server.
<p align="center">
	<img src="../img/pipeline-giov2api-deploy.png">
</p>

## Staging Deployment Note
Already publish code to staging please do this :

1. Create pull request without prefix `WIP:`
2. List your workitems on descriptions.
   Give tag `close #issue_number` to close automatically after pull request accepted.
3. Assignee your team to review your code 

Meanwhile if you dont want deploy on staging : 

1. Only push your code to your active branch
2. Dont create pull request to master
3. If you already create pull request on git, edit your pull request with title `WIP:`   
