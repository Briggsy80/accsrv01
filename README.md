# Assetto Corsa Server Setup
 Dedicated Server setup on Linux -Ubuntu 16.04 +,
After running in trouble installing ACserver I thought I put a little guide together. My server is Ubuntu, but I think you can use it on any other linux distro. Only to install the needed 32 bit libraries you have to use the installation repositories and commands of your Linux ditribution.

Most Ubuntu installations today are 64bit.
As Steam is a 32 bit installation, first we have to install some 32 bit libraries to make the installation process work properly.
You can install it wherever you like, but I will explain it here as it would be installed in
/home/steam/assetto/

sudo apt-get update  
sudo apt-get install lib32gcc1 wine-development

The following library is needed for stracker, if used  
sudo apt-get install zlib1g:i386          
sudo mkdir  /home/steam     
chown user: group /home/steam -R  

use name and group of the user name and group with root rights. This is important, because sometimes the execution of ./steamcmd.sh aborts with an error, if there is no root permission to read from and write to steam subdirectories.

sudo chmod -R 755 /home/steam/  
cd /home/steam  
wget http://media.steampowered.com/client/steamcmd_linux.tar.gz  
tar -xvf steamcmd_linux.tar.gz  
rm steamcmd_linux.tar.gz  
./steamcmd.sh +@sSteamCmdForcePlatformType windows  

You will get into the steam console  
  
Steam> login <username>;  
Steam> passwd  
Steam> enter security code sent to you registration email of your steam account  
Steam> force_install_dir ./assetto  
Steam> app_update 1430110  
Steam> exit  
 
to configure track, cars, ports, name of your ACC host  
nano /home/steam/assetto/cfg/server_cfg.ini  

to configure your car list  
nano /home/steam/assetto/cfg/entry_list.ini  
  
start the server after configuration and needed ports are open with  
wine ./accServer.exe  

 
  
https://www.acc-wiki.info/wiki/Server_Configuration
