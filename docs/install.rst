===========================
Installing Google Assistant
===========================


1. Follow the instructions here_  to configure a developer project and account settings.

   .. _here: https://developers.google.com/assistant/sdk/guides/library/python/embed/config-dev-project-and-account
   Then follow this guide_  to register the device and obtain the credentials.json file. Refer to the video below for step by step guidelines.
   
   .. _guide: https://developers.google.com/assistant/sdk/guides/library/python/embed/register-device

   
.. raw:: html

    <div style="text-align: center; margin-bottom: 2em;">
    <iframe width="100%" height="350" src="https://www.youtube.com/embed/dMNtmp8z52M?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
    </div>


2. Place the credentials.json file in/home/${USER}/ directory **DO NOT RENAME**


3. Use the one-line installer for installing Google Assistant.
   3.1 Change directory::

          cd /home/${USER}/

   3.2 Make the installer Executable::

          sudo chmod +x ./GassistPi/scripts/gassist-installer.sh

   3.3 Execute the installer::

          sudo  ./GassistPi/scripts/gassist-installer.sh

   **When Prompted, enter your Google Cloud console Project-Id, A name for your Assistant and the Full path to the credentials file, including the json extension.**


4. Copy the google assistant authentication link from terminal and authorize using your google account.   


5. Copy the authorization code from browser onto the terminal and press enter.   


6. After successful authentication, the Google Assistant Demo test will automatically start.
   At the start, the volume might be low, the assistant volume is independent of the Pi volume, increase the volume by using "Hey Google, Set volume to maximum" command.   
  

7. After verifying the working of assistant, close and exit the terminal.
