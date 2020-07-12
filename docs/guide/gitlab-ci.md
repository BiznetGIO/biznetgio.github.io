We define 2 stage deploy project to public, staging and production.


## Restricted Rule
1. Dont create new branch except from master.
2. Dont create pull request except to master.
3. Define prefix `WIP:` to avoid project owner merge your code if you not done yet.
4. Perhaps if you still change your code and unmerge pull request, 
   edit your pull request title with prefix `WIP:`   


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

## Deploy Staging 
Already publish code to staging please do this :

1. Create pull request without prefix `WIP:`
2. List your workitems on descriptions.
   Give tag `close #issue_number` to close automatically after pull request accepted.
3. Assignee your team to review your code 

Meanwhile if you dont want deploy on staging : 

1. Only push your code to your active branch
2. Dont create pull request to master
3. Set pull request with title `WIP:`   

## Deploy Production
1. On monorepo project, change your version on file `version`
2. On legacy repositories, tag your version and commit push to new version 
