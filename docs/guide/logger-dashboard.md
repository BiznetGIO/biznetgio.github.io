We provide logs to tracking your project running on server. 
Produce logs contain with standard out and error logs messages. 
So may this will help you debug code when getting some issues.


### Staging Logs
Staging logs served by kibana dashboard on https://log.biznetgio.dev/. 
Trace some logs can be viewed realtime as in your browser. 
You can filter specific service name by find out from `orcinus.yml` on your project folder.

#### sample 1:
Find logs with contain service name by typing service name on search tab. 

<p align="center">
	<img src="../img/logs-contain-name.png">
</p>


#### sample 2:
Find logs with specific service name by typing `docker.name:<exact service name>`.
An exact service name can find on `orcinus.yml`

<p align="center">
	<img src="../img/orcinus-service-name.png">
</p>


<p align="center">
	<img src="../img/logs-specific-name.png">
</p>

## Production Logs
We don't produce stream production logs like on staging. 
You can request from gitlab as pipeline and logs will viewed as jobs tty.

<p align="justify">
<img src="../img/step1-produce-logs-production.png">
1. Click button pipeline to create a new pipeline job
</br></br>

<img src="../img/step2-produce-logs-production.png">
2. Set variabel with `SERVICE_NAME` with value service name. 
This service name can found on `orcinus-production.yml`  
</br></br>

<img src="../img/step3-produce-logs-production.png">
3. Pipeline job will created and procced
</br></br>

<img src="../img/step4-produce-logs-production.png">
4. Pipeline will show logs service name from production. 
Click button complete raw to show logs as text detail. 
Due limit size of jobs logs, you can only download 500kb file logs.
</p>