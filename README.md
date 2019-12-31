# What it is

This directory provides tunable configuration variables
and files for the NGS-MSTB deployment as a service with 
the `docker-compose.yaml` and wrapper script `docker_deploy.sh`
from `ngs-mstb-docker` repository.

There are common configuration files in the current directory,
and host-specific configuration files under `hosts` subdirectory.
The variables defined under `hosts` take precedence.

The configs for each host should go into a subdirectory under
`hosts` named after the fully qualified domain name of the target
host.

For example, you might have testing and production hosts 
configured this way.

** The intent of this repository is that you customize it,
assign Git tag to your deployed config commit, it and keep 
your fork secret because it contains passwords and admin keys
for your deployed Galaxy instances **

Currently, a host `localhost` exists as an example.

The SSL key and certificate under `localhost` are self-signed.
They were copied from the upstream Galaxy Docker image. They will
have the same effect as not having them here at all. In such case,
if the variable `USE_HTTPS=True`, the Galaxy user will see a warning about the
untrusted certificates and have to click through to get past the warning.

You can customize the `welcome.html` and the branding variable in the configs.

*Note* that both the certificates and the `welcome.html` will be copied on the
first start of the container. If you remove them later, and you run the container
exporting Galaxy data onto a permanent bind-mount, the old copies will still be
used after the container is restarted.


