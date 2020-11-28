====================
Updating the project
====================


1. Change directory::

     cd /home/${USER}/

2. Make the update script executable::

     sudo chmod +x /home/${USER}/GassistPi/scripts/update.sh

4. Run the update script::

     sudo /home/${USER}/GassistPi/scripts/update.sh

5. If there is an update available, the project will be updated else the script will make a smooth exit.

6. If the Project is updated, reconfigure the **config.yaml** file.

.. note::
 The update script will make a backup of your existing project folder before updating eg. GassistPi.bak-xxxx-xx-xx**
