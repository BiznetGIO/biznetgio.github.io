When service already deploy and run on staging, we can bind service on your local computers with tunneling.
This method give many advantages: 

- show all running up service and some informations on staging
- simulate our ready up staging service to local development 
- make use of some staging service can access from local dev without installing service that nedeed
- access shared data or variables on staging store like redis, elastic, etc...


## Tunneling Concepts
```bash
local dev <--> allowed docker container host <--> staging server host
```

1. local dev is our computer for real, requesting a staging service through from allowed container
2. allowed container host will forward to staging host, some permissions may disabled due for limitations access 
3. staging server accept request from allowed container host, back then forward the service from allowed container requested  

## Command
```bash
./bgn-dev remote 
```

<p align="center">
	<img src="../img/bgn-dev-remote.png">
</p>


## Show all running service on staging server
First, show service that exist on staging to ensure list service ready up.

`bgn-dev remote list`  or `bgn-dev remote ls`

This will return some informations like service name, port, container id and source addess of container.  

<p align="center">
	<img src="../img/bgn-dev-remote-ls.png">
</p>

## Tunnel Service 
1. Connect a staging project to local development(1 service) 
 
`bgn-dev project remote <local port:staging_service_name:staging_port>`

1. `local port` is our local port computers, bind any port depending on your local available port
2. `staging_service_name` can define from lookup `NAME` from remote list
3. `staging_port` can define from lookup `PORT` from remote list, this port is from container service. 

!!! info
	if there are no port on informations list, you can find hardcoded on `orcinus.yml` 
	or expose port on `Dockerfile` from base service name project. 

## Example
### 1. Tunnel a service to local development 
Remote a service name `giov2-api` to local development.

`bgn-dev project remote 5858:giov2-api:5000`

<p align="center">
	<img src="../img/bgn-dev-remote-giov2api-tunnel.png">
</p>

After success create tunneling, by `curl` or even open the browser and entry address `localhost:port_tunnel` 

<p align="center">
	<img src="../img/bgn-dev-remote-giov2-api-check.png">
</p>

### 2. Tunnel more than one service to local development 
Some case you need more than one service can be used on local development. 
You can tunneling with sparated commas by commands:

`bgn-dev project remote <local port:staging_service_name:staging_port>,<local port:staging_service_name:staging_port>,etc...`

<p align="center">
	<img src="../img/bgn-dev-remote-by-commas.png">
</p>
