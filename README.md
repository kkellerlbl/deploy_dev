# deploy_dev
Tools for deploying a KBase development environment in docker containers

## Prerequisites

A functioning deployment currently requires around 40GB of disk space available and 8GB of memory in the Docker machine. For instructions on preparing a deployment environment (installing docker and opening ports) please refer to the README at [README-buildenv.md](README-buildenv.md)

## Clone this repo

    git clone https://github.com/kbaseIncubator/deploy_dev.git

## Create an initial site config

    cd deploy_dev
    cp site.cfg.example site.cfg

## Edit site.cfg

    USER=<your KBase developer username>
    PASSWORD=<your KBase developer password>
    PUBLIC_ADDRESS=<public IP or public hostname of your machine>

Note that your docker machine needs to be accessible from your web browser, because this is how you will get to your Narratives; it also has to be resolvable within the docker container.

## Run the bootstrap script to start things up

    ./deploy.sh

This will take about 20 minutes to run. If you encounter problems when trying to deploy, you can look at the [README-deploy](README-deploy.md) file that describes in detail the steps that are performed by the deployment script.

If everything completes successfully, it will tell you the URL at which you can see your narrative instance, e.g., "Point your browser to: https://\<publichostname\>:6443/. But visit https://\<publichostname\>:8443/services/ first to accept the SSL certificate."

If the deploy script hangs, you may need to kill it and reset (see the "Resetting" section below).

----

## Resetting

Sometimes the deployment fails, and you need to start over. Run the reset script before you try again:
    ./scripts/reset.sh
 
## Starting a client container (optional)

If you want to start a client container, use the client.sh script. It will run as your user id using your home directory. 

    ./scripts/client.sh
    
# More Resources

Consult the [docs](docs) directory for more information.  You can find more details on developing in the deploy_dev environment in [README-developing.md](./docs/README-developing.md).

You can find tips for debugging in [docs/README-debugging](docs/README-debugging.md).
