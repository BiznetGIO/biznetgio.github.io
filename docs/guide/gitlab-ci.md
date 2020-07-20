We define 2 stage deploy project to public, staging and production. 

Furthermore, we also provide automation code inspector with SonarQube. 
SonarQube tools help you to monitoring some bugs, vulnerability and reliability code inside your project. 


## Restricted Rule
1. Dont create new branch except from master.
2. Dont create pull request except to master.
3. Define prefix `WIP:` to avoid project owner merge your code if you not done yet.
4. Perhaps if you still change your code and unmerge pull request, 
   edit your pull request title with prefix `WIP:`   

!!! important
	Creating new branch without rebasing from master will miss some latest code. 
	Before continue on your working branch, always fetch first and rebase with master.
	Still confuse with this? Check git tips and ticks [here](git-tutorial.md). 


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

## gitlab-ci for Production
Generate a gitlab-ci file staging with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-production <your-awesome-project>
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

## Production Deployment
1. On monorepo project, change your version on file `version`
2. On legacy repositories, tag your version and commit push to new version 
