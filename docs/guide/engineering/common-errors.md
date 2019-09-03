# Common Errors

---

## Docker

- `ERROR: Couldn't connect to Docker daemon at http+docker://localunixsocket - is it running? `

Add your current user to docker group then activates new permissions [for docker
group](https://github.com/docker/compose/issues/4181#issuecomment-523127214)

``` bash
sudo usermod -a -G docker $USER
newgrp docker
```

## Virtual machine

- can't do `ssh` or `scp` to CentOS remote vm

[Change](https://stackoverflow.com/a/39635200/6000005) `PasswordAuthentication`
in `/etc/ssh/sshd_config`

``` bash
'PasswordAuthentication no'
# to
'PasswordAuthentication yes'
```

then restart the service `sudo systemctl restart sshd`

