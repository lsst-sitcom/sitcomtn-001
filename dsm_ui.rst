Using the Monitor UI
====================

The DSM laptop contains the software to run the monitoring user interface (UI). It is installed within a `miniconda <https://docs.conda.io/en/latest/miniconda.html>`_ environment. To setup the environment for running the UI, perform the following from a terminal.

.. _ui-env:

.. prompt:: bash
  
  mc
  conda activate dsm 

The UI is configured via one of the files contained in the `/dsm/dsm_ui_config` directory. This directory is a clone of this `GitHub repository <https://github.com/lsst-com/dsm_ui_config>`_ and contains the standard configurations for the DSM. To run the default configuration of the UI, do the following from a terminal (after running the :ref:`steps above <ui-env>`.).

.. prompt:: bash

  smm_ui -c /dsm/dsm_ui_config/default.yaml

Installing a New UI Version
---------------------------

Should it become necessary to install a new version of the UI, first perform the steps :ref:`here <ui-env>` and then run the following.

.. prompt:: bash

  pip install spot_motion_monitor

If a new version is available, it will be installed.
