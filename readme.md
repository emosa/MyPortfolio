#Portfolio Deployment Plan

##New Server Procedure

###1.Create Server
+ Configured to the Development Guidelines specifications for this class

###2. SSH Into the Server
+ ssh root@Server_IP_Address
+ Enter password

###3. Create Non-Root User
+ adduser Username
+ adduser Username sudo

###4. End SSH Session
+ exit

###5. Login as Non-Root User
+ ssh Username@Server_IP_Address
+ Enter password

###6. Update Package System
+ sudo apt-get update
+ Enter password

###7. Upgrade Package System
+ sudo apt-get upgrade

###8. Update Packages for Newly Installed Version
+ sudo apt-get update

###9. Update System level Packages
+ sudo aptitude update
+ sudo aptitude safe-upgrade
+ sudo reboot

###10. Install Packages
+ Git
	+ See Git: Install & Config
+ Apache
	+ See Apache Install & Config

##Git: Install & Config

###1. Install Git
+ sudo apt-get install git-core

###2. Configure Git
+ git config --global user.name “NAME”
+ git config --global user.email Your@Email.com

###3. Confirm Settings
+ git config --list

###4. Create SSH Keys for Github Access
+ ssh-keygen -t rsa -C ”YourEmail@example.com”
	+ This will ask if you want to customize the name, you don’t. Just press enter.
+ Enter a passphrase
+ Re-enter the passphrase

###5. Put the RSA key on file with github.com so this server is treated as a trusted machine.
+ less ~/.ssh/id_rsa.pub
	+Copy ALL of the contents of this file to your clipboard.
+ Add new SSH Key to your Github account under the Account Settings.
	+ Click the Add Key button
	+ Enter a title defining the server
	+ Paste the RSA file’s contents into text area marked “Key”
	+ Click Add Key

## Apache Install & Config
###1. Install Apache 2
+ sudo apt-get install apache2

###2. Configure ServerName
+ Restart Server
	+ sudo service apache2 restart
+ Failed to Restart
	+ apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

+ Configure ServerName
	+ sudo pico /etc/apache2/conf.d/security
		+ Add
			+ ServerName localhost
	+ sudo service apache2 restart
	+ Apache should report a successful restart

###3. Restrict Access
+ sudo pico /etc/apache2/conf.d/security
	+ Uncomment <Directory />
	+ Add
		+ Options FollowSymLinks
	+ sudo service apache2 restart

###4. Change Permissions to Allow Access
		+ sudo chown -R UserName /var/www

		