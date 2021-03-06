#################
Configuring audio
#################

.. note::
 - Non-Raspberry Pi users and users using other setups, choose the USB-DAC option.
 - The speaker-test command is used to initialize alsa, so please do not skip that.
 - AIY-HAT users, please reboot the Pi at places mentioned, else it will lead to audio and taskbar issues.
 - Those using any other DACs or HATs install the cards as per the manufacturer's guide and then you can use the USB-DAC config file after changing the hardware ids.
 - Respeaker users, please do not use their official setup for this project.


*******************************************************
Choose the audio configuration according to your setup
*******************************************************
Non-Raspbian users install Alsa first::

        sudo apt-get install alsa-utils


Users on Raspberry Pi OS Prior to Dec 2020 Release
====================================================

USB DAC or USB Sound Card Users
---------------------------------
Run the following in the terminal::

     sudo apt-get update
     cd /home/${USER}/
     sudo chmod +x ./GassistPi/audio-drivers/USB-DAC/scripts/disable-onboard.sh
     sudo ./GassistPi/audio-drivers/USB-DAC/scripts/disable-onboard.sh
     sudo reboot
     cd /home/${USER}/
     sudo chmod +x ./GassistPi/audio-drivers/USB-DAC/scripts/install-usb-dac.sh
     sudo ./GassistPi/audio-drivers/USB-DAC/scripts/install-usb-dac.sh
     speaker-test


AIY-HAT Users
---------------------------------
Run the following in the terminal::

     sudo apt-get update
     cd /home/${USER}/
     sudo chmod +x ./GassistPi/audio-drivers/AIY-HAT/scripts/configure-driver.sh
     sudo ./GassistPi/audio-drivers/AIY-HAT/scripts/configure-driver.sh
     sudo reboot
     cd /home/${USER}/
     sudo chmod +x ./GassistPi/audio-drivers/AIY-HAT/scripts/install-alsa-config.sh
     sudo ./GassistPi/audio-drivers/AIY-HAT/scripts/install-alsa-config.sh
     speaker-test


AIY-VOICE-BONNET Users
---------------------------------
Run the following in the terminal::

    sudo apt-get update
    cd /home/${USER}/
    sudo chmod +x ./GassistPi/audio-drivers/AIY-VOICE-BONNET/scripts/configure-driver.sh
    sudo ./GassistPi/audio-drivers/AIY-VOICE-BONNET/scripts/configure-driver.sh
    sudo reboot
    cd /home/${USER}/
    sudo chmod +x ./GassistPi/audio-drivers/AIY-VOICE-BONNET/scripts/install-alsa-config.sh
    sudo ./GassistPi/audio-drivers/AIY-VOICE-BONNET/scripts/install-alsa-config.sh
    speaker-test

.. note::
  Pi users using a release between May 2020 and Dec 2020:
   - Copy the USB-MIC-HDMI and USB-MIC-JACK folders from the /Extras/May2020 directory and paste them in the audio-drivers directory and then proceed with the instructions below.

USB Mic and HDMI Users
---------------------------------
Run the following in the terminal::

      sudo apt-get update
      cd /home/${USER}/
      sudo chmod +x ./GassistPi/audio-drivers/USB-MIC-HDMI/scripts/configure.sh
      sudo ./GassistPi/audio-drivers/USB-MIC-HDMI/scripts/configure.sh
      sudo reboot
      cd /home/${USER}/
      sudo chmod +x ./GassistPi/audio-drivers/USB-MIC-HDMI/scripts/install-usb-mic-hdmi.sh
      sudo ./GassistPi/audio-drivers/USB-MIC-HDMI/scripts/install-usb-mic-hdmi.sh
      speaker-test


USB Mic and Audio Jack Users
---------------------------------
Run the following in the terminal::

       sudo apt-get update
       cd /home/${USER}/
       sudo chmod +x ./GassistPi/audio-drivers/USB-MIC-JACK/scripts/usb-mic-onboard-jack.sh
       sudo ./GassistPi/audio-drivers/USB-MIC-JACK/scripts/usb-mic-onboard-jack.sh
       speaker-test


Custom Voice HAT Users
---------------------------------
Run the following in the terminal::

       sudo apt-get update
       cd /home/${USER}/
       sudo chmod +x ./GassistPi/audio-drivers/CUSTOM-VOICE-HAT/scripts/install-i2s.sh
       sudo ./GassistPi/audio-drivers/CUSTOM-VOICE-HAT/scripts/install-i2s.sh
       sudo reboot
       cd /home/${USER}/
       sudo chmod +x ./GassistPi/audio-drivers/CUSTOM-VOICE-HAT/scripts/custom-voice-hat.sh
       sudo ./GassistPi/audio-drivers/CUSTOM-VOICE-HAT/scripts/custom-voice-hat.sh
       speaker-test


Respeaker/Waveshare/Raspiaudio 2 Mic HAT Users
---------------------------------
Run the following in the terminal::

       sudo apt-get update
       cd /home/${USER}/
       git clone https://github.com/shivasiddharth/WM8960-Audio-HAT
       cd ./WM8960-Audio-HAT/   
       sudo ./install.sh    
Before restarting, run::     

       sudo nano /etc/pulse/default.pa    
In that, add the following lines and save::    

       load-module module-alsa-source device = hw: 0,0
       load-module module-alsa-sink     
Now, you can reboot::     

       sudo reboot
       speaker-test


Users on Raspberry Pi OS Dec 2020 Release or After
====================================================


USB DAC or USB Sound Card or USB Mic Users
------------------------------------------
From Dec 2020 release, USB audio devices are plug and play.
  1. Insert your USB device.
  2. Right click on the audio/speaker icon on the bar at the top.
  3. Select your Audio Input and Audio Output device.


AIY-HAT Users
---------------------------------
Run the following in the terminal::

     sudo apt-get update
     cd /home/${USER}/
     sudo chmod +x ./GassistPi/audio-drivers/AIY-HAT/scripts/configure-driver.sh
     sudo ./GassistPi/audio-drivers/AIY-HAT/scripts/configure-driver.sh
     sudo reboot
     speaker-test


AIY-VOICE-BONNET Users
---------------------------------
Run the following in the terminal::

    sudo apt-get update
    cd /home/${USER}/
    sudo chmod +x ./GassistPi/audio-drivers/AIY-VOICE-BONNET/scripts/configure-driver.sh
    sudo ./GassistPi/audio-drivers/AIY-VOICE-BONNET/scripts/configure-driver.sh
    sudo reboot
    speaker-test


Custom Voice HAT Users
---------------------------------
Run the following in the terminal::

     sudo apt-get update
     cd /home/${USER}/
     sudo chmod +x ./GassistPi/audio-drivers/CUSTOM-VOICE-HAT/scripts/install-i2s.sh
     sudo ./GassistPi/audio-drivers/CUSTOM-VOICE-HAT/scripts/install-i2s.sh
     sudo reboot
     speaker-test


Respeaker/Waveshare/Raspiaudio 2 Mic HAT Users
---------------------------------
Run the following in the terminal::

       sudo apt-get update
       cd /home/${USER}/
       git clone https://github.com/shivasiddharth/WM8960-Audio-HAT
       cd ./WM8960-Audio-HAT/   
       sudo ./install.sh    
Before restarting, run::     

       sudo nano /etc/pulse/default.pa    
In that, add the following lines and save::    

       load-module module-alsa-source device = hw: 0,0
       load-module module-alsa-sink     
Now, you can reboot::     

       sudo reboot
       speaker-test

