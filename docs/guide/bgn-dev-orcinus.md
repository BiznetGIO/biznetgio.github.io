Modern deployment need take fast and efficient manageable process workflow. 
Meanwhile, containerize apps one of solutions to driven fast software delivery. 
Making as containerize make legacy apps running without limitations from enviroment hosts, reliable delivery and scalable runtime.

Containerize apps not enough when apps ready to deliver. 
Common issued appear when developer spend many time to setup their applications, it will getting worst if company has contain many project. 
We introduce `Container Production Environment(CPE)` to manage our deployment. 
This CPE stage adopt from modern software development lifecycle, aim for simplify entire our project run and deploy. 
CPE enviroment scope build and running of the application using an existing orcinus file. 
Means, it ready support with AutoDevops concept, CPE will run automatically detect, build, test, deploy and monitor base on where stage you deploy, staging or production.  

### Orcinus
Orcinus is opensource simple orchestration management tools already support k8s (kubernetes).
With orcinus file present configurations, container image, service name, enviroment and some configurations can handled infrastructure within code/config. 

### Infrastructure as Code (IaC) 
Orcinus already support to describe your infrastructure within orcinus yaml file. 
It means, you allowed to managing your infrastructure operations environment by adjusting whatever you applied.

Look some sample figure here.

#### Figure 1
<p align="center">
    <img src="../img/orcinus-figure1.png">
</p>
Node 1, Node 2, Node 3 and Node-n describe a physical server configurations connected with a single network manager.
We define stack enviroment named `Orcinus Stack`. 
When you on same stack, you allowed access other service name just by call their service name. 
In other words, same stack is same as in network manager.   

#### Figure 2
<p align="center">
    <img src="../img/orcinus-figure2.png">
</p>
In other case, we need to allowed your service connect and access in public internet.   
Set traefik port same with enviroment variables. And setup your enviroment domain same with traefik.frontend.rule.

Feel interest about orcinus tools? Check our wiki [here](https://github.com/orcinustools/orcinus/wiki)   

----

### Orcinus file on monorepo project
Orcinus file with extension yaml format (.yml) required to run with orcinus tools. 
Container Production Enviroment as AutoDevops will automatically detect to deploy and running a container service.   

### Generated orcinus file
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
        - API_PORT=5000
      commands: ["sh","run.sh", "server", "development"]

```

- `stack` : name of stack, if a service up in a same stack you can access by call the service name.
- all configurations on services define their service itself include variables, enviroment, script and so on. 
- `image: my-awesome-project:dev` : name of container image that will be running on deployment
- `ports` : expose virtual port to host port 
- `environment` : some var related to setup or service configurations
- `commands` : run service, this step should do when you running the service

By default, a service run with orcinus will act like auto-healing on kubernetes. You can prevent this with add
```
      restart_policy:
          condition: "none"
```  


## Credits
[https://github.com/orcinustools](https://github.com/orcinustools)
