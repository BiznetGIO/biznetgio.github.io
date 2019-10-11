# RESTKnot Setup

## Installations

- Install etcd & knot

``` bash
apt install knot libknot8 etcd
```

- Start knot & etcd

``` bash
sudo systemctl start etcd
sudo systemctl start knot

# check if they are running
sudo systemctl status etcd
sudo systemctl status knot
```

- Run kafka & zookeeper (using docker container)

create file docker-compose.yml which contains:

```
version: '3'
services:
  zookeeper:
    image: wurstmeister/zookeeper
  kafka:
    image: wurstmeister/kafka
    ports:
      - "9092:9092"
    environment:
      KAFKA_ADVERTISED_HOST_NAME: localhost
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
```
Then run it with:

``` bash
docker-compose up
```

## Setups

### Setup knot

``` bash
sudo knotc conf-init # trigger knot db to save configs
```

### Setup the RESTKnot agent

``` bash
# create venv
mkvirtualenv rest-knot --python=/usr/bin/python3.7


# install agent dependencies
cd RESTKnot/agent/
pip install -r requirements.txt
pip install -e .
```

- Set broker and knot value

``` bash
sudo /home/azzamsya/.virtualenvs/rest-knot/bin/dnsagent envi broker
sudo /home/azzamsya/.virtualenvs/rest-knot/bin/dnsagent envi knot
```

Value example:

!!! info

    Each operating system has different location of `libknot.so` and it's
    socket, so check it carefully.

``` bash
# knot env value example
OS_KNOT_LIB=libknot.so
OS_KNOT_SOCKS=/var/run/knot/knot.sock

#  broker env value example
OS_BROKER=localhost
OS_PORTS=9092
OS_TOPIC=domaindata
OS_FLAGS=master
OS_GROUP=cmgz_master
```

- Check value

``` bash
sudo /home/azzamsya/.virtualenvs/rest-knot/bin/dnsagent envi show -e broker
```

- Start the agent

``` bash
sudo /home/azzamsya/.virtualenvs/rest-knot/bin/dnsagent start master
```


### Setup the RESTKnot API

- Install API dependencies

``` bash
cd RESTKnot/api/
pip install -r requirements.txt
pip install -e .
```

- Populate data to etcd

``` bash
cd RESTKnot/api/
python migrate_db.py 
```

- Run RESTKnot API

``` bash
# for development
sh run.sh server development

# for production
sh run.sh server production
```

## Test the result

``` bash
$ curl 127.0.0.1:5000/api/zone/list

{
   "code":200,
   "count":1,
   "data":[
      {
         "key":"1",
         "value":"example1.com",
         "created_at":"2019-09-30 20:05:13.486640",
         "user":{
            "key":"1",
            "email":"admin@foo.com",
            "project_id":"001",
            "state":"inserted",
            "created_at":"2019-07-20 23:04:22.420505"
         }
      }
   ],
   "Status":"success",
   "message":"Operation
succeeded"
}

```
