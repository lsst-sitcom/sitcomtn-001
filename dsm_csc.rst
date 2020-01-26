Dome Seeing Monitor CSC
=================================

Using the CSC
-------------

The DSM laptop has a Docker container installed on it that houses the Commandable SAL Component (CSC) software. There is also a Docker Compose file that aids in launching the container. That file provides the following container instances:

* dsm1-fast-sim
* dsm2-slow-sim
* dsm1
* dsm2

The sim containers are the CSC running in simulated mode. The fast simulator feeds telemetry at 1 Hz. The slow simulator feeds telemetry at once every 30 seconds. The other two containers are the realtime ones for the (currently) two DSM units planned. These containers are used in conjunction with the DSM UI. Since the CSC is an indexed component, when running multiple containers, one must ensure that only one of each index is running at any given time. Each laptop assigned to a DSM unit should be responsible for running only one of the realtime CSC containers to avoid conflicts with telemetry entering the EFD.

Startup CSC
+++++++++++

.. prompt:: bash

  cd /dsm/ts_Dockerfiles/Compose/TusconTestStand/DSM
  docker-compose up dsm1

If a container is already present, the above will generate an error message. To force a new container, do the following.

.. prompt:: bash

  docker-compose up --force-recreate dsm1

Shutdown CSC
++++++++++++

The following can be run from anywhere

.. prompt:: bash

  docker exec -it <container> /home/saluser/.shutdown.sh

The <container> refers to the running CSC that is to be shutdown. If all containers are shutdown, the containers themselves should be removed by doing the following.

.. prompt:: bash

  cd /dsm/ts_Dockerfiles/Compose/TusconTestStand/DSM
  docker-compose down

.. warning::
  The down command destroys ALL running containers.

Update the Docker Container
---------------------------

If a new update to the container is necessary, the following command can be run to perform the update.

.. prompt:: bash

  docker pull lsstts/dsm:<tag>

The <tag> will depend on the desired version of the container to update. To list the currently deployed images, run the following.

.. prompt:: bash

  docker images


