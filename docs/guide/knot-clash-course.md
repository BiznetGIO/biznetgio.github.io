# Knot Clash Course

## Quickstart

installation:

```bash
$ sudo apt-get install knot
```

run knot:

``` bash
$ sudo systemctl start knot

# to check if it's running
$ sudo systemctl status knot
```

## Server Login

- copy the key and put it into a  `key.pem` file
- change it's mode: `chmod 600 key.pem`
- get your server ip (.e.g from your horizon portal)
- log to your machine using ssh


``` bash
$ ssh -i key.pem centos@<your ip master>
```

Accessible machine (the one that had the public Ips) are only the slaves. To
access the servers that had private IPs (including master). Use the key file
inside the slave servers.

- to log to server that didn't have public IPs.

``` bash
[centos@cmg01z00knsl001 ~]$ ls   # this in in master server
STAGING  STAGING.tar.gz  vm-key.pem

[centos@cmg01z00knsl001 ~]$ ssh -i vm-key.pem centos@<slave ip>
[centos@vultr-test-1 ~]$  # logged into slave server
```

We use the following format, to name our servers:

``` bash
<serverlocation|servernumber|purpose|rule|number>

e.g:
cmg01z00knms001: for master
cmg01z00knsl001: for slave
```

## Knot Setups

- Ensure all old files removed 

!!! warning

    Do this only if you knot what you are doing, otherwise jump directly to "start
    adding zone" at the next step"


``` bash
rm -rf * /var/lib/knot # knot database
rm -rf * /etc/knot # knot config
rm -rf * /run/knot # knot socket 
```

- start the knot

``` bash
# systemctl start knot
```

The initial file of knot (after removing all contents in `/var/lib/knot/` and
`/etc/knot/`) are only the `timers` directory in `/var/lib/knot/`

- start adding zone (or other things)

``` bash
sudo knotc conf-init
```

Start `knotc conf-init`. This step only requered if you have fresh knot installation.

This will add `confdb` directory in `/var/lib/knot/`.

To check the content of knot database, you can do export it to the file:

``` bash
# knotc conf-export /etc/knot/knot.conf

# to check it's content
# cat /etc/knot/knot.conf
```

## Add your zone (simple example)


``` bash
# knotc conf-begin ## start every command with `*-begin`
OK

# knotc conf-set server.version "None of your bussiness"
OK

# knotc conf-set server.listen "0.0.0.0@53"
OK

# knotc conf-commit  ## end every command with `*-commit`
OK

# knotc conf-read # to see knot db content
server.version = None of your bussiness
server.listen = 0.0.0.0@53
```

This will put the value to knot database. To export it to file (e.g knot.conf)
you can do `knotc conf-export /etc/knot/knot.conf`.

But entering value one by one using `knotc` is tedious. You can add them to a
file in:

``` bash
/etc/knot.conf
```

then import to the knot db:

``` bash
knotc conf-import knot.conf
```

## Adding SOA (example)

``` bash
# knotc zone-begin lapar.io

# knotc zone-set lapar.io. @ 86400 SOA
ns1.biz.net.id. hostmaster.biz.net.id. 2018070410 10800 3600 604800 38400

# knotc zone-commit lapar.io
OK

# check if it's okay
# knotc zone-read lapar.io
[lapar.io.] lapar.io. 86400 SOA ns1.biz.net.id. hostmaster.biz.net.id. 2018070410 10800 3600 604800 38400
```

## Adding NS (example)

``` bash
# knotc zone-begin lapar.io
OK

# knotc zone-set lapar.io. @ 14000 NS ns1.biznet.id.
OK

# knotc zone-commit lapar.io

# knotc zone-read lapar.io
[lapar.io.] lapar.io. 14000 NS ns1.biznet.id.
[lapar.io.] lapar.io. 86400 SOA ns1.biz.net.id. hostmaster.biz.net.id. 2018070411 10800 3600 604800 38400
```

## Adding A (example)


``` bash
# knotc zone-begin lapar.io
OK

# knotc zone-set lapar.io. @ 3600 A 127.0.0.1

# knotc zone-commit lapar.io
```

## Testing the result

``` bash
kdig @localhost lapar.io SOA +tcp
kdig @localhost lapar.io A +tcp
```

## Additional information

To learn more consult [knot documentation](https://knot.readthedocs.io/en/stable/operation.html)
