Orcinus is simple orchestration management tools already support k8s (kubernetes).
We'd happy for all container service run and deploy with orcinus in our server. 

Feel interest about orcinus tools? Check our wiki [here](https://github.com/orcinustools/orcinus/wiki)   


### Orcinus file on monorepo project
Orcinus file with extension yaml format (.yml) required to run with orcinus tools.

Then inside your project, we already generated 3 orcinus file. 

1. `orcinus-dev.yml`: orcinus file to run on your local development
2. `orcinus.yml`: orcinus file to run on staging
3. `orcinus-production.yml`: orcinus file to run on productions

### Structure monorepo project
```bash
  .
	your-awesomeproject    # monorepo project
	├── <generated from boilerplate code>
	├── orcinus-dev.yml  
	├── orcinus.yml  
	├── orcinus-production.yml
	└── version 
```

!!! note
	File `version` is not auto generated, you need to add this when ready to production. 
	Change this file with version base on your history release production.

### Orcinus yml file example
This file sample from generated orcinus-dev.yml 
```
stack: "orcinus"
services:
    my-awesome-project:
      image: my-awesome-project:dev
      ports:
        - "5000:5000"
      environment:
        - API_URL="http://foo/api/v1"
        - API_KEY="This secret key"
      commands: ["sh","run.sh", "server", "development"]

```
By default, a service run with orcinus will act like auto-healing on kubernetes. You can prevent this with add
```
      restart_policy:
          condition: "none"
```  


## Credits
[https://github.com/orcinustools](https://github.com/orcinustools)