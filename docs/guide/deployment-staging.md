We define 2 stage deploy project to public, staging and production. 
Staging is internal release, this phase proccess to test and review by product owner. 
After apps ready successfully runnning on staging, all feature will be check according with product documentations.
This step make sure of all functional feature works normally before move to productions.

## gitlab-ci for Test Code
This step will add your project to SonarQube within on this [link](https://cq.biznetgio.dev/). 
Generate a gitlab-ci file test with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-test <your-awesome-project>
```

## gitlab-ci for Staging
Generate a gitlab-ci file staging with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-staging <your-awesome-project>
```


## Staging Deployment 
Already publish code to staging please do this :

1. Create pull request without prefix `WIP:`
2. List your workitems on descriptions.
   Give tag `close #issue_number` to close automatically after pull request accepted.
3. Assignee your team to review your code 

Meanwhile if you dont want deploy on staging : 

1. Only push your code to your active branch
2. Dont create pull request to master
3. Set pull request with title `WIP:`   
