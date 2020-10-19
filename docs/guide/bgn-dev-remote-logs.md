Staging logs can access by remote logs with bgn tools. 
This will help you check some error logs as realtime on terminal. 

## Staging Remote Logs 
First find service name with remote list command. 
Already explain from this tutorial: [bgn dev show remote service](bgn-dev-remote-tunnel.md#show-all-running-service-on-staging-server)
Then do with this command below:

```
./bgn-dev remote logs <service_name>
```

<p align="center">
	<img src="../img/bgn-dev-logs-giov2api.png">
</p>


