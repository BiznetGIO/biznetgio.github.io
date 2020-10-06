We define 2 stage deploy project to public, staging and production. 
Staging is internal release, this phase proccess to test and review by product owner. 
After apps ready successfully runnning on staging, all feature will be check according with product documentations.
This step make sure of all functional feature works normally before move to productions.

## Staging Phase
When developer ready up their code onto server, we determine 4 step on gitlab ci/cd. 
 - test
 - build
 - release
 - deploy
 
This step will calls pipeline gitlab to verify each step done or unsuccesfull. 
If either one or some step fail, another next step can not be procceed. 

### 1. test 
test pipeline is check and verify with internal test and sonarqube. Common project microservice/backend python include with testing code, pytest or unittest to testing functional and libraries. By default test pipeline will send project to sonarqube, output can be viewed on our [sonarqube site](https://cq.biznetgio.dev/). 
Adding testing on gitlab-ci just easy, you can use `bgn-dev tools` as describe before. 
#### gitlab-ci for Test Code
This step will add your project to SonarQube within on this [link](https://cq.biznetgio.dev/). 
Generate a gitlab-ci file test with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-test <your-awesome-project>
```

### 2. build
Build pipeline is step when containerize the applications. It will build container image base on `Dockerfile` that include on your project folder. 

### 3. release
Release pipeline is step push/upload successfull image built to our registry image. 
This step register an image container with tag `latest` and ready to deploy on staging server. 

### 4. deploy
This final step to running your containerize applications on staging server. 
It will automatically detect `orcinus.yml` on container production enviroment and up onto staging server.
Step build, release and deploy will not run if you dont add staging gitlab ci file. You can generate with `bgn-dev tools` as describe before.  
#### gitlab-ci for Staging
Generate a gitlab-ci file staging with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-staging <your-awesome-project>
```

!!!important
   on monorepo project please contact deployment team to generate gitlab ci file to avoid conflict file  

## Staging Deployment Note
Already publish code to staging please do this :

1. Create pull request without prefix `WIP:`
2. List your workitems on descriptions.
   Give tag `close #issue_number` to close automatically after pull request accepted.
3. Assignee your team to review your code 

Meanwhile if you dont want deploy on staging : 

1. Only push your code to your active branch
2. Dont create pull request to master
3. Set pull request with title `WIP:`   
