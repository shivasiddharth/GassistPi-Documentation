========================================
Guide to use the customizations/features
========================================


Enabling or disabling custom actions
------------------------------------

Major custom actions have been provided with a control key or switch in the **config.yaml**.
Set it to **Enabled** to enable the custom actions and set it to **Disabled** to disable them.


Using custom actions in Non-English languages
---------------------------------------------

1. Languages supported: French, Italian, Spanish, Dutch, German and Swedish.

2. In the **config.yaml** file, under the **Languages and Choice** option set your desired language.

3. Use the Translated versions of the English syntaxes given for all the custom actions.

4. You can change the keywords/trigger words for the custom actions in the keywords file.


Controlling Sonoff-Tasmota, Domoticz devices from Google Home
-------------------------------------------------------------

1. This has been implemented using Adafruit_IO.
2. Create an acount and a feed in adafruit.io website.
3. Enter those details in the config.yaml file.
4. Register or login into IFTTT_ and create an applet to send commands from google assistant to adafruit_io feed.

   .. _IFTTT: http://www.ifttt.com/
5. For controlling domoticz and sonoff devices, the adafruit.io command should match the syntaxes for the respective custom actions.


Using the interpreter mode
--------------------------

.. note:: THIS MAKES USE OF GOOGLE CLOUD SPEECH API. FREE USAGE IS LIMITED TO 60MINS/MONTH. FOR MORE DETAILS ON THE USAGE LIMITS CHECK THIS_ LINK

.. _THIS: https://cloud.google.com/speech-to-text/pricing
1. Go to the projects page_ on your Google Cloud Console.

   .. _page: https://console.cloud.google.com/project
2. Select your project from the list.
3. On the left top corner, click on the hamburger icon or three horizontal stacked lines.
4. From the **API and services** option, select library and in the search bar type **speech**, select **Cloud Speech API** and click on "ENABLE".
5. You will be prompted to create a billing account if you already have not created one. Follow the onscreen instructions to create a billing account and then Enabled the API.
6. Create a service account and generate credentials.
7. Copy the downloaded the JSON key and place it /home/pi/ directory **DO NOT RENAME**.
8. Enter the path to the Key along with the key name Eg: /home/pi/xxxx.json  in the config.yaml file in the "Google_Cloud_Speech_Credentials_Path" field under "Speechtotext".
   You can use one key for Cloud Speech and Cloud Text to Speech, but should enter the same path seperately in config.yaml

**Command Syntax:**

To start the interpreter::

   Hey Google, Start __Your_Desired_Language__ interpreter.
To stop the interpreter::

   Hey Google, Stop interpreter.



Using google cloud text to speech
---------------------------------

.. note:: GOOGLE CLOUD TEXT TO SPEECH HAS A LIMITED USAGE ACCESS. ONCE THE QUOTA IS EXHAUSTED, THE PROJECT WILL AUTOMATICALLY SWITCH TO gTTS.

1. Go to the projects page_ on your Google Cloud Console.

   .. _page: https://console.cloud.google.com/project
2. Select your project from the list.
3. On the left top corner, click on the hamburger icon or three horizontal stacked lines.
4. "From the API and services" option, select library and in the search bar type text, select "Cloud Text-to-Speech API" and click on "ENABLE".
5. In the API window, click on "Credentials" and then on "+ Create Credential".
6. In the "Add credentials to your project" window, in step-1 under "Which API are you using?" drop down choose "Cloud Text-to-Speech API" and down below choose "No, I’m not using them". Then click on "What credentials do I need?"
7. In step-2 give your service account a name and on the right in the "Role" drop down choose Project-->Owner and under "Key Type" select "JSON" and click "Continue".
8. Copy the downloaded key and place it /home/pi/ directory DO NOT RENAME.
9. Enter the path to the Key along with the key name Eg: /home/pi/xxxx.json  in the config.yaml file in the "Google_Cloud_TTS_Credentials_Path" field.
   You can use one key for Cloud Speech and Cloud Text to Speech, but should enter the same path seperately in config.yaml


Controlling assistant/sending preset commands using IR remote
------------------------------------------------------

1. Connect the IR Receiver according to the wiring diagram given below.

.. note:: The diagram given is for GPIO 17, if you are using another GPIO, please make the suitable changes to the connection.   


.. figure:: ../_static/images/IRWiring.jpg
    :align: center
    :figwidth: 300px
    :target: ../_static/images/IRWiring.jpg  
    

2. Run the sample IR receiver script to get the codes for your desired buttons::  

      python /home/${USER}/GassistPi/Extras/IR-Sensor.py

3. In the config.yaml under IR, list your codes and corresponding queries/actions. The number of queries should match the number of codes listed.

4. If you want to execute the custom actions like Spotify, YouTube playback, Domoticz Control etc, prefix the word custom. 
   
   Eg::
   
       custom Play God's Plan from Youtube
       custom Turn On __Domoticz device name__
       custom Play all the songs from Google Music

5. If you are sending a command to be processed by google assistant, there is no need to prefix custom. 
   
   Eg::
   
       what is the time
       what can you do for me

Video for reference:

   .. raw:: html

       <div style="text-align: center; margin-bottom: 2em;">
       <iframe width="100%" height="350" src="https://www.youtube.com/embed/LlbcjkRuQZk?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
       </div>
