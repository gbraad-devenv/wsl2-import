Import instructions for WSL2
============================

```
PS> podman pull ghcr.io/gbraad-devenv/fedora/systemd:38 
PS> podman run --name devenv-systemd ghcr.io/gbraad-devenv/fedora/systemd:38 echo
PS> podman export devenv-systemd -o devenv-systemd.tar
PS> podman rm devenv-systemd
PS> wsl --import devsys c:\Users\gbraad\devsys .\devenv-systemd.tar
PS> wsl --set-default devsys
PS> wsl exec echo -e "[user]\ndefault=gbraad\n[boot]\nsystemd=true" > /etc/wsl.conf
PS> wsl --terminate devsys
PS> wsl
$ sudo dnf install -y podman
$ sudo rpm --restore shadow-utils
$ podman ps
WARN[0002] "/" is not a shared mount, this could cause issues or missing mounts w
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
```

`.wslconfig`
```
[wsl2]
processors=2
```

Note: do not use `save` as this preserves layers and will cause the import to fail (be incomplete).
