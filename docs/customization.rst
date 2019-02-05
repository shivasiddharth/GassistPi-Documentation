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

**NOTE: THIS MAKES USE OF GOOGLE CLOUD SPEECH API. FREE USAGE IS LIMITED TO 60MINS/MONTH. FOR MORE DETAILS ON THE USAGE LIMITS CHECK THIS LINK_**

  .. _LINK: https://cloud.google.com/speech-to-text/pricing

1. Go to the projects page on your Google Cloud Console-> https://console.cloud.google.com/project
2. Select your project from the list.
3. On the left top corner, click on the hamburger icon or three horizontal stacked lines.
4. From the **API and services** option, select library and in the search bar type **speech**, select **Cloud Speech API** and click on "ENABLE".
5. You will be prompted to create a billing account if you already have not created one. Follow the onscreen instructions to create a billing account and then Enabled the API.
6. Create a service account and generate credentials.
7. Copy the downloaded the JSON key and place it /home/pi/ directory **DO NOT RENAME**.
8. Enter the path to the Key along with the key name Eg: /home/pi/xxxx.json  in the config.yaml file in the "Google_Cloud_Speech_Credentials_Path" field under "Speechtotext" (you can use one key for Cloud Speech and Cloud Text to Speech, but should enter the same path seperately in config.yaml).

**Command Syntax:**
To start the interpreter::

   Hey Google, Start __Your_Desired_Language__ interpreter.

To stop the interpreter::

   Hey Google, Stop interpreter.


   
