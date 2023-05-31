

##  Uninstalling docker rootless gave the following output

``` console
mikkel@stingray ~> /usr/bin/dockerd-rootless-setuptool.sh uninstall      (base) 
+ systemctl --user stop docker.service
+ systemctl --user disable docker.service
Removed /home/mikkel/.config/systemd/user/default.target.wants/docker.service.
[INFO] Uninstalled docker.service
[INFO] Deleted CLI context "rootless"
Current context is now "default"
[INFO] Configured CLI to use the "default" context.
[INFO] 
[INFO] Make sure to unset or update the environment PATH, DOCKER_HOST, and DOCKER_CONTEXT environment variables if you have added them to `~/.bashrc`.
[INFO] This uninstallation tool does NOT remove Docker binaries and data.
[INFO] To remove data, run: `/usr/bin/rootlesskit rm -rf /home/mikkel/.local/share/docker`
```

Is `docker.service` a rootless thing?
What does rootless do with PATH, DOCKER_HOST and DOCKER_CONTEXT and what are these?

## Previously on docker
The following daemon.json was used previously

``` json
{ 
   "group": "docker",
   "data-root": "/volumenta/docker",
   "dns": ["172.30.130.75"],
   "dns-search": ["stingray.local"],
   "storage-driver": "overlay2"
}
```

# FAQ

##  Installing/uninstalling rootless docker shutdown issue

Doing `/usr/bin/dockerd-rootless-setuptool.sh [install|uninstall]` some times fails with docker.sock being active. Doing `sudo systemctl disable --now docker.service docker.socket containerd.service` + reboot shuts it down properly.

## Docker host issue with rootless

Rootless docker had an issue with not being able to contact this socket `set -gx DOCKER_HOST unix:///run/user/1000/docker.sock`. It was configured in `~/.config/fish/config.fish`.

## Dockerd, docker cli and contexts

One docker docker-cli can communicate with multiple docker daemons (locally docker engine vs docker desktop or local vs remote). This multiplexing is done through the [docker-context](https://docs.docker.com/engine/context/working-with-contexts)

use `docker context ls` to see what docker contexts are available.

## SubUID and SubGID setup and how it is setup

is discussed [here](https://docs.docker.com/desktop/faqs/linuxfaqs/#how-do-i-enable-file-sharing)

