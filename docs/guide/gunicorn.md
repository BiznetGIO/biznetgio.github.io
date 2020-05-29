# Gunicorn Best Practice


## Prefix
Gunicorn is a Python WSGI HTTP Server that usually lives between a reverse proxy (e.g., Nginx) or load balancer (e.g., AWS ELB) and a web application such as Django or Flask.


## Gunicorn Improve Performance
`To improve performance when using Gunicorn we have to keep in mind 3 means of concurrency.`

### 1. workers.
Basic fundamental for handling concurrency process using by workers. The suggested number of workers is `(2*CPU)+1`.

If we are using a dual-core(2 CPU) machine, 5 is the suggested workers value.
``` bash
gunicorn --workers=5 main:app
```
### 2. threads on workers.
Each workers allow have multiple threads when python application running. If we implement threads to workers, by default worker class set is to `gthread`. 

The suggested maximum concurrent requests when using workers and threads is still`(2*CPU)+1`.

If we are using a dual-core(2 CPU) machine and we want to use a mix of workers and threads, we could use 5 workers and 1 threads, to get 5 maximum concurrent requests.
```bash
gunicorn --workers=5 --threads=1 main:app
```
it same as :
```bash
gunicorn --workers=5 --threads=1 --worker-class=gthread main:app
```

### 3. pseudo-threads.
There are some Python libraries such as gevent and Asyncio that enable concurrency in Python by using `pseudo-threads` implemented with coroutines.

Gunicorn allows for the usage of these asynchronous Python libraries by setting their corresponding worker class.

Here the settings that would work for a single core machine that we want to run using gevent:

```bash
gunicorn --worker-class=gevent --worker-connections=1000 --workers=3 main:app
```

!!! info
	`worker-connections` is a specific setting for the gevent worker class. See also worker class on  https://docs.gunicorn.org/en/stable/settings.html#worker-class

`(2*CPU)+1` is still the suggested `workers` since we only have 1 core, we’ll be using 3 workers.

In this case, the maximum number of concurrent requests is 3000 (3 workers * 1000 connections per worker)

## Credits
https://medium.com/building-the-system/gunicorn-3-means-of-concurrency-efbb547674b7
https://docs.gunicorn.org/en/stable/settings.html#worker-processes