Import instructions for WSL2
============================


### Image import
```
PS> wsl --import devsys c:\Users\gbraad\devsys .\devenv-systemd.tar
PS> wsl --set-default devsys
PS> wsl exec echo -e "[user]\ndefault=gbraad\n[boot]\nsystemd=true" > /etc/wsl.conf
PS> wsl --terminate devsys
PS> wsl
```

### Fixes
```
$ sudo dnf install -y podman
$ sudo rpm --restore shadow-utils
$ podman ps
WARN[0002] "/" is not a shared mount, this could cause issues or missing mounts w
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
```

### Set up Podman from host

```
PS> podman system connection add devuser ssh://gbraad@localhost/run/user/1000/podman/podman.sock --identity c:\Users\gbraad\.ssh\id_rsa
PS> podman system connection add devroot ssh://root@localhost/run/podman/podman.sock --identity c:\Users\gbraad\.ssh\id_rsa
PS> podman -c devuser ps -a
```
