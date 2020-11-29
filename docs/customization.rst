========================================
Guide to use the customizations/features
========================================



Enabling or Disabling Custom Actions
------------------------------------

Major custom actions have been provided with a control key or switch in the **config.yaml**.
Set it to **Enabled** to enable the custom actions and set it to **Disabled** to disable them.



Using Custom Actions in Non-English Languages
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



Using the Interpreter Mode
--------------------------

.. note:: THIS MAKES USE OF GOOGLE CLOUD SPEECH API. FREE USAGE IS LIMITED TO 60MINS/MONTH. FOR MORE DETAILS ON THE USAGE LIMITS CHECK THIS_ LINK

.. _THIS: https://cloud.google.com/speech-to-text/pricing
1. Go to the projects page_ on your Google Cloud Console.

   .. _page: https://console.cloud.google.com/project
2. Select your project from the list.
3. On the left top corner, click on the hamburger icon or three horizontal stacked lines.
4. From the **API and services** option, select library and in the search bar type **speech**, select **Cloud Speech API** and click on "ENABLE".
5. You will be prompted to create a billing account if you already have not created one. Follow the onscreen instructions to create a billing account and then Enable the API.
6. Create a service account and generate credentials.
7. Copy the downloaded the JSON key and place it /home/pi/ directory **DO NOT RENAME**.
8. Enter the path to the Key along with the key name Eg: /home/pi/xxxx.json  in the config.yaml file in the "Google_Cloud_Speech_Credentials_Path" field under "Speechtotext".
   You can use one key for Cloud Speech and Cloud Text to Speech, but should enter the same path seperately in config.yaml

**Command Syntax:**

To start the interpreter::

   Hey Google, Start __Your-Desired-Language__ interpreter.

To stop the interpreter::

   Hey Google, Stop interpreter.



Using Google Cloud Text to Speech
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
9. Enter the path to the Key along with the key name Eg: /home/pi/xxxx.json  in the config.yaml file in the **Google_Cloud_TTS_Credentials_Path** field.
   You can use one key for Cloud Speech and Cloud Text to Speech, but should enter the same path seperately in config.yaml



Adding Custom Search API and Generating API Key
-----------------------------------------------
1. Go to the projects page_ on your Google Cloud Console.

   .. _page: https://console.cloud.google.com/project
2. Select your project from the list.
3. On the left top corner, click on the hamburger icon or three horizontal stacked lines.
4. Move your mouse pointer over **API and services** and choose **Credentials**.
5. Click on create credentials and select API Key and choose close. Make a note of the created API Key and enter it in the config.yaml script at the indicated location.
6. "From the API and services" option, select library and in the search bar type **search**, select **Custom Search API** API and click on "ENABLE".
7. In the API window, click on "All API Credentials" and in the drop down, make sure to have a tick (check mark) against the API Key that you just generated.



Adding YouTube Data API and Generating API Key
-----------------------------------------------
1. Go to the projects page_ on your Google Cloud Console.

   .. _page: https://console.cloud.google.com/project
2. Select your project from the list.
3. On the left top corner, click on the hamburger icon or three horizontal stacked lines.
4. Move your mouse pointer over **API and services** and choose **Credentials**.
5. Click on create credentials and select API Key and choose close. Make a note of the created API Key and enter it in the config.yaml script at the indicated location.
6. "From the API and services" option, select library and in the search bar type **youtube**, select **YouTube Data API v3** API and click on "ENABLE".
7. In the API window, click on "All API Credentials" and in the drop down, make sure to have a tick (check mark) against the API Key that you just generated.



.. note:: If a custom action uses both Custom Search and YouTube API, you need to enable both the APIs but only one API KEY needs to be generated.

.. note:: The same API key can be used for all the associated custom actions.



Controlling Assistant or Sending Preset Commands Using IR Remote
------------------------------------------------------

1. Connect the IR Receiver according to the wiring diagram given below.

.. figure:: ../docs/_static/images/IRWiring.jpg
    :align: center
    :scale: 40%
    :target: ../docs/_static/images/IRWiring.jpg

.. note:: The diagram given is for GPIO 17, if you are using another GPIO, please make the suitable changes to the connection.

2. Run the sample IR receiver script to get the codes for your desired buttons::

      python /home/${USER}/GassistPi/Extras/IR-Sensor.py

3. In the config.yaml under IR, list your codes and corresponding queries/actions. The number of queries should match the number of codes listed.

4. If you want to execute the custom actions like Spotify, YouTube playback, Domoticz Control etc, prefix the word custom.

   Eg::

       custom Play God's Plan from Youtube
       custom Turn On _Domoticz-device-name__
       custom Play all the songs from Google Music

5. If you are sending a command to be processed by google assistant, there is no need to prefix custom.

   Eg::

       what is the time
       what can you do for me

 **Video for reference:**

   .. raw:: html

       <div style="text-align: center; margin-bottom: 2em;">
       <iframe width="100%" height="350" src="https://www.youtube.com/embed/LlbcjkRuQZk?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
       </div>



Sending Commands or Queries to Google Assistant Over MQTT
------------------------------------------------------

1. Set up your desired MQTT broker.
   If you are setting up Raspberry Pi as a MQTT broker, follow the guide below.

   .. raw:: html

       <div style="text-align: center; margin-bottom: 2em;">
       <iframe width="100%" height="350" src="https://www.youtube.com/embed/Ce2Djxx9shU?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
       </div>

2. Enter the MQTT broker credentials and subscription topic in the provided config.yaml file.
3. Set the **MQTT_Control** to **Enabled**.
4. Now, you can send queries or commands to google assistant over MQTT.
5. If you are sending a command for custom actions, prefix custom in the payload.

   Eg::

       custom Play God's Plan from Youtube
       custom Turn On __Domoticz-device-name__
       custom Play all the songs from Google Music

6. If you are sending a command to be processed by google assistant, there is no need to prefix custom.

   Eg::

       what is the time
       what can you do for me

7. To turn on/off microphone just send the simple command mute.

   Eg::

       mute

  **For more details on the how to use this feature, refer to the video below:**

  .. raw:: html

      <div style="text-align: center; margin-bottom: 2em;">
      <iframe width="100%" height="350" src="https://www.youtube.com/embed/oemsmrdhNP8?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
      </div>



Streaming Music from Deezer
---------------------------

.. note:: As a roundabout approach, I have programmed the assistant to get the playlist details using Deezer API and then fetch those tracks from YouTube.
  This feature uses a YouTube Data API v3.
  Click :ref: here<https://gassistpi-documentation.readthedocs.io/en/latest/customization.html#adding-youtube-data-api-and-generating-api-key> for guidelines to add YouTube Data API to the project and to generate the required key.

1. Add your Deezer user number in the config.yaml under the **Deezer:** and **User_id**.

2. In the config.yaml, under **Google_cloud_api_key:** replace **ENTER-YOUR-GOOGLE-CLOUD-API-KEY-HERE** with the key from Google Cloud Console.

**Command Syntax:**

To play the playlists added to your Deezer account::

      Hey Google, Play playlist __playlist-number__ from Deezer.

Example::

      Hey Google, Play __playlist 1__ from Deezer



Streaming Music from Gaana.com
------------------------------

.. note:: As a roundabout approach, I have programmed the assistant to get the playlist details using Deezer API and then fetch those tracks from YouTube.
  This feature uses both YouTube Data API v3 and Custom Search API.
  Click here_ for guidelines to add YouTube Data API to the project and to generate the required key.

  .. _here: https://gassistpi-documentation.readthedocs.io/en/latest/customization.html#adding-youtube-data-api-and-generating-api-key
  Click here_ for guidelines to add Custom Search API to the project and to generate the required key.

  .. _here: https://gassistpi-documentation.readthedocs.io/en/latest/customization.html#adding-custom-search-api-and-generating-api-key
1. Add your playlists in the config.yaml under **Gaana: and Playlists:**.

2. In the config.yaml, under **Google_cloud_api_key:** replace **ENTER-YOUR-GOOGLE-CLOUD-API-KEY-HERE** with the key from Google Cloud Console.

**Command Syntax:**

1. To play the playlists added in config.yaml file::

      Hey Google, Play playlist __playlist-number__ from Gaana.com

   Example::

      Hey Google, Play __playlist 1__ from Gaana.com

2. To play other playlists::

      Hey Google, Play __user-playlist-query__ from Gaana.com

    Example::

      Hey Google, Play __Bollywood top 50__ from Gaana.com



Controlling Domoticz Devices
----------------------------

.. note:: As of today, you can control lights and switches only, more controls will be added in the future.

1. In the config.yaml file under **Domoticz:** change **Domoticz_Control:** from **Disabled** to **Enabled**.
2. List the device names and the ids that you want to control in the config.yaml file.
   The names should be the same as the ones in the domoticz server.

**Command Syntax:**

1. To On/Off/Toggle::

      Hey Google, Turn On/Turn Off/Toggle  __Name of your light__

   Example::

      Hey Google, Turn On __Bedroom Lamp__

2. To Change Brightness (between 0 and 100)::

      Hey Google, Set  __Name of your light__ brightness to __desired value__

   Example::

      Hey Google, Set __Bedroom lamp__ brightness to __5__

3. To Change  Colour (refer the list of available colors_)::

      Hey Google, Set  _Name of your light_ color to __desired color__
      Hey Google, Change  __Name of your light__ to __desired color__ color

   .. _colors: https://gassistpi-documentation.readthedocs.io/en/latest/colorlist.html#list-of-available-colors-for-home-automation-projects

   Example::

      Hey Google, Set __Bedroom lamp__ color to __red__
      Hey Google, Change __Bedroom lamp__ to __red__ color



Custom Conversations
----------------------------

1. Customize the assistant's reply to a specific question.
2. Add the list of questions and answers in config.yaml under the **Conversation**: option.
3. **There must be only one question, but corresponding answers can be as many**.
4. Sample questions and answers has been provided, please follow the same pattern.



Custom Wakeword Activation
----------------------------

1. You can choose to either Enable or Disable the custom wakeword activation in the config.yaml file.
2. In the config.yaml file, under Wakewords, change the **"Custom_Wakeword"** to **'Enabled'** if you want to use the custom wakeword or set it to 'Disabled' if you dont want to use the custom wakeword option.
3. You have a choice between Snowboy and Picovoice for the custom wakeword engine.
4. For Snowboy, change **"Wakeword_Engine"** to **Snowboy** and for Picovoice, change **"Wakeword_Engine"** to **Picovoice**.
5. For changes to take effect, you need to restart the assistant. Changing status while an instance of assistant is already running will not cause any change.
6. Create your custom snowboy model here_. Add the models to **/GassistPi/src/resources/snowboy_models** directory.
.. _here: https://snowboy.kitt.ai
7. Sample Snowboy and Picovoice models have been provided and placed in the /GassistPi/src/resources/ folder. Set your desired models by setting their paths in the config.yaml file.
8. To disable the default **"Ok Google"** hotword, set the Ok_Google option to **"Disabled"**.

.. note:: If you turn off the default **Ok Google** wakeword/hotword, everytime you invoke the assistant using the custom wakeword, you will get a prompt for the Mic being turned Off and On.

9. Users using pushbutton.py or Pi Zero users have an option between using custom wakeword and GPIO trigerring. If custom wakeword is enabled, then GPIO trigger will not work. To enable GPIO triggering, set custom wakeword to 'Disabled'.



Playing Spotify Playlist
----------------------------

.. note:: Spotify API currently only supports playback in a web browser, but DRM content is being blocked in the Raspberry Pi. As a roundabout approach, I have programmed the assistant to get the playlist details using Spotipy API and then fetch those tracks from YouTube. This custom program has a better accuracy than spotify playlist playback using mpsyt.
          This feature uses a YouTube Data API v3. Click here_ for guidelines to add YouTube Data API to the project and to generate the required key.
.. _here: https://gassistpi-documentation.readthedocs.io/en/latest/customization.html#adding-youtube-data-api-and-generating-api-key

1. Click here_ and register for a spotify developer account, if you already don't have one.
.. _here: https://developer.spotify.com/dashboard/login
2. In the developer's dashboard, choose **CREATE A CLIENT ID**. In the pop-up window provide the requested details.
3. Click on the new app created and copy the **CLIENT ID** and **CLIENT SECRET**. Paste it in the config.yaml file in the indicated space.
4. Access spotify here_ and copy the username to be entered in config.yaml.
.. _here: https://www.spotify.com/account/overview/

**Command Syntax:**
To play your playlist::

   Hey Google, Play __user-playlist-query__  from Spotify

 Example::

   Hey Google, Play __Workout playlist__ from Spotify

   Hey Google, Play __Top Dance Numbers__ from Spotify

.. note:: If your playlist name does not have the word **playlist** do not use that in the query.



Tracking Kickstarter Campaigns
--------------------------------
A custom Google search engine for Kickstarter_ has been used. This requires an API to be added to your existing project.
.. _Kickstarter: https://www.kickstarter.com/

Click here_ for guidelines to add Custom Search API to the project and to generate the required key.
.. _here: https://gassistpi-documentation.readthedocs.io/en/latest/customization.html#adding-custom-search-api-and-generating-api-key

**Command Syntax:**
To track a kickstarter campaign::

   Hey Google, Track __your-desired-campaign__ Kickstarter campaign

   Hey Google, What is the status of __your-desired-campaign__ Kickstarter campaign


 Example::

   Hey Google, Track __Mycroft 2__ Kickstarter campaign

   Hey Google, What is the status of __Mycroft 2__ Kickstarter campaign
