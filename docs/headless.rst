================================================
Headless Google Assistant
================================================


Setting up Google Assistant to auto start on boot
-------------------------------------------------

1. Open the service files in the /GassistPi/systemd/ directory and verify your project and model ids and save the file.

2. Change directory::

       cd /home/${USER}


3. Make the service installer executable::

      sudo chmod +x ./GassistPi/scripts/service-installer.sh


4. Run the service installer::

      sudo ./GassistPi/scripts/service-installer.sh


5. Enable the service::

      sudo systemctl enable gassistpi.service


6. Start the service::

      sudo systemctl start gassistpi.service


Steps to manually start the assistant
-------------------------------------

At any point of time, if you wish to manually start the assistant:

1. Stop the service if it is already running::

      sudo systemctl stop gassistpi.service


2. **Ok-Google Hotword/Pi3/Pi2/Armv7 users**    
     Open a terminal and execute the following::

      /home/${USER}/env/bin/python -u /home/${USER}/GassistPi/src/main.py --device_model_id 'replace this with the model id'


3. **Pushbutton/Pi Zero/Pi B+ and other Non-Armv7 users**   
     Open a terminal and execute the following::

     /home/${USER}/env/bin/python -u /home/${USER}/GassistPi/src/pushbutton.py --project-id 'replace this with your project id'  --device-model-id 'replace this with the model id'

Insert your Project Id and Model Id in quotes in the mentioned places


Disabling assistant's auto start
--------------------------------

At any point of time, if you wish to stop the auto start of the assistant:      

Open a terminal and execute the following::

      sudo systemctl stop gassistpi.service
      sudo systemctl disable gassistpi.service
