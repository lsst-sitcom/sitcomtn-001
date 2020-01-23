Dome Seeing Monitor UI
======================

Using the UI
------------

The DSM laptop contains the software to run the monitoring user interface (UI). It is installed within a `miniconda <https://docs.conda.io/en/latest/miniconda.html>`_ environment. To setup the environment for running the UI, perform the following from a terminal.

.. _ui-env:

.. prompt:: bash
  
  mc
  conda activate dsm 

The UI is configured via one of the files contained in the `/dsm/dsm_ui_config` directory. This directory is a clone of this `GitHub repository <https://github.com/lsst-sitcom/dsm_ui_config>`_ and contains the standard configurations for the DSM. To run the default configuration of the UI, do the following from a terminal (after running the :ref:`steps above <ui-env>`.).

.. prompt:: bash

  smm_ui -c /dsm/dsm_ui_config/default.yaml

Installing a New UI Version
---------------------------

Should it become necessary to install a new version of the UI, you must switch into the `dsm` service account by first doing the following.

.. prompt:: bash

  sudo su -s /bin/bash dsm

Next, perform the steps to :ref:`setup the environment <ui-env>` and then run the following.

.. prompt:: bash

  pip install -U spot_motion_monitor

If a new version is available, it will be installed.

Installing a Development Version
--------------------------------

If it becomes necessary to install a development version of the UI, first create a directory called `git` in your home directory. Next, `cd` into that and execute the following.

.. prompt:: bash

  git clone https://github.com/lsst-sitcom/spot_motion_monitor.git

If you intend to commit changes back to the repository and have the privileges to do so, clone the repository this way.

.. prompt:: bash

  git clone git@github.com:lsst-sitcom/spot_motion_monitor.git

Next change into the directory of the clone and checkout the branch that you want to run. Example is shown below.

.. prompt:: bash

  cd spot_motion_monitor
  git checkout -t origin/tickets/SE-1302

Once on the correct branch, perform the following steps to run the UI.

.. prompt:: bash

  mc
  conda activate dsm_dev
  python setup.py build_ui
  rsmm python scripts/run.py

The `rsmm` wrapper sets up the environment to correctly execute the program. The CLI options from `smm_ui` are all available in this mode. The third step is only necessary when changing branches. The last step is necessary on subsequent executions of the UI.
