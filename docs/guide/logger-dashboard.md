We provide logs to tracking your project running on server. 
Produce logs contain with standard out and error logs messages. 
So may this will help you debug code when getting some issues.


## Staging Logs
Staging logs can access by remote logs with bgn tools. 
This will help you check some error logs as realtime on terminal. 

First find service name with remote list command. 
Already explain from this tutorial: [bgn dev show remote service](bgn-dev-remote-tunnel.md#show-all-running-service-on-staging-server)
Then do with this command below:

```
./bgn-dev remote logs <service_name>
```

<p align="center">
	<img src="../img/bgn-dev-logs-giov2api.png">
</p>

    

## Production Logs
We don't produce stream production logs like on staging. 
You can request from gitlab as pipeline and logs will viewed as jobs tty.

<p align="justify">
<img src="../img/step1-produce-logs-production.png">
1. Click button pipeline to create a new pipeline job
</br></br>

<img src="../img/step2-produce-logs-production.png">
2. Set variabel with <b>SERVICE_NAME</b> with value service name. 
This service name can be found in <b>orcinus-production.yml</b>  
</br></br>

<img src="../img/step3-produce-logs-production.png">
3. Pipeline job will created and procced
</br></br>

<img src="../img/step4-produce-logs-production.png">
4. Pipeline will show logs service name from production. 
Click button complete raw to show logs as text detail. 
Due limit size of jobs logs, you can only download 500kb file logs.
</p>