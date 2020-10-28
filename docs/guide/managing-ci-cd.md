Deploy applications on development may need takes up time. 
Become unusefull when the jobs be like repetitive works.CI/CD concepts ideology solve this with execute some script and automate on running machine.

 - CI short from Continuous Integration, this practice when developers finish their code push and merge on online repository. 
 	Developers can shared their changes code in several times for a sometime  
 - CD short from Continuous Delivery, this automate the entire applications release process. 
 - and other means CD is Continuous Deploy, on gitlab this automate when applications ready serve and running onto server (may staging or production)  

refence : [gitlab ci/cd](https://docs.gitlab.com/ee/ci/introduction/)


We do here works with gitlab, we provide integrate tools with gitlab ci/cd.
This present short a simplicity to manage create `gitlab-ci.yaml` without limitations.

### bgn-dev ci 
Use command with `bgn-dev` tools
```bash
	./bgn-dev ci
```

<p align="center">
	<img src="../img/bgn-dev-ci.png">
</p>

### listing project stage
To make sure of your project ready on autodevops enviroment, check with `bgn-dev` tools
```bash
  ./bgn-dev ci list <your-awesome-project>
```
example show listed project `svc-ms-gio-v2` already registered on gitlab-ci:
```bash
	./bgn-dev ci list svc-ms-gio-v2
```	
This will print output :
<p align="center">
	<img src="../img/bgn-dev-list-giov2api.png">
</p>

### gitlab-ci for Test
Generate a gitlab-ci file test with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-test <your-awesome-project>
```

### gitlab-ci for Staging
Generate a gitlab-ci file staging with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-staging <your-awesome-project>
```

### gitlab-ci for Production
Generate a gitlab-ci file production with `bgn-dev` tools
```bash
  ./bgn-dev ci generate-production <your-awesome-project>
```

### gitlab-ci rebuild
some case conflicted `gitlab-ci.yml` you can rebuild with command:
```bash
  ./bgn-dev ci rebuild
```

!!!important
   	on monorepo project please contact deployment team to generate gitlab ci file to avoid conflict file 
 
