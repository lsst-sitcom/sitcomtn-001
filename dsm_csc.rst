Dome Seeing Monitor CSC
=================================

Using the CSC
-------------

Startup CSC
+++++++++++

.. prompt:: bash

  cd /dsm/ts_Dockerfiles/Compose/TusconTestStand/DSM
  docker-compose up dsm1

Shutdown CSC
++++++++++++

Following can be run from anywhere

.. prompt:: bash

  docker exec -it dsm1 /home/saluser/.shutdown.sh
