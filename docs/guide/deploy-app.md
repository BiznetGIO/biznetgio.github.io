# Deploying Application

---

## Create your Virtual Machine

- login into [https://horizon.neo.id/](https://horizon.neo.id/). Ask the
credential to your team.

- create new vm:
    - go to "compute → instances", select "launch instance"
    - fill appropriate "instance name" and other fields.
    - choose CentOS in "source" for the sake of similarity.
    - choose your flavour size
    - ask your team what "network" to use.
    - ask your team what "security group" to use.
    - ask your team what "keypair" to use.
    - Ignore "network prort", "configuration", "server group", "scheduler", and
    "metadata" for now.
    - select "launch instance"

## Get your private key

- get the "private-key" by visiting "orchestration → stack → your-vm-key → overview"
- copy that "private-key" to write that to a file with appropriate name in your
  local machine. e.g key.pem
- run `chmod 600 key.pem`

## Accessing your VM

Do it with ssh:

- `ssh -i /path/to/your/vm-key.pem <your-vm-username>@<public-ip>`

then do your business there. Commonly installing `docker` and `docker-compose`

``` bash
sudo yum install docker # installing docker

# installing docker-compose (yes, it's not in centos repo)
sudo yum install epel-release
sudo yum install -y python-pip
sudo pip install docker-compose
```

## Taking your image to your vm

!!! Note

    It's advicable to avoid using Docker Hub for our development image. It's
    also not suitable way of doing managing internal projects.

Use `scp` for the win!

Sadly, `scp` [will not work seamlessly in centos](https://stackoverflow.com/a/39635200/6000005).
You need to change:

``` bash
'PasswordAuthentication no'
# to
'PasswordAuthentication yes'
```

in "/etc/ssh/sshd_config", then re-started the service `sudo systemctl restart sshd`

### Prepare your image to be transferred using SCP

- [save docker as tar](https://stackoverflow.com/a/23938978/6000005)

    `docker save -o <path for generated tar file> <image name>`

- move from your local machine to remote vm

    `scp -i /path/to/key.pem whois-api.tar <username>@<public-ip>:~/your/destination/dir/`

- `cd` to your "destionation/dir" then load the image

    `docker load -i <path to image tar file>`

## Run the app

Run the app as you did in local machine

`$ docker-compose up`
