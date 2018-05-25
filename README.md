# ha-linux-server-config
A project for the requirements of Udacity FSND

### Step A: The Lightsail instance  
#### 1. Create a Lightsail instance in AWS
* Click on the “Services” link in the top navbar
* Under the “Compute section, select Lightsail
* Inside the Lightsail page, click on “Create instance” page
* Under “Select Blueprint” section click on “OS Only”
* Select “Ubuntu”
* Select a plan. Usually the first basic plan, free for the first month then $5 afterwards
* Under “Name your instance”, rename your instance if you wish to
* Click the “Create” button. The instance will take few moments to appear on the instances page  
#### 2. Download the Lightsail default private key to local device
* In the instances page click on the instance name to open the settings page.
* Scroll all the way down to the bottom of the page and click on the blue “Account page” link
*Click on “download” at the bottom of the page, name and save the file on your local device then ssh into your Lightsail server : sudo ssh ubuntu@35.178.90.82 -i lighsail_key.pem -p 2200 )  
#### 3. Add ports 2200/tcp and 123/udp
* On your instance page click on the “Networking” tab,
* Under “Firewall” section, click on “+Add another” at the bottom of the ports list,
* Add ports as follow: Custom: TCP:2200, and Custom:UDP:123. (after adding these two ports the list should include at least four ports, 22, 80, 2200, and 123)
* Click “Save”

#### 4. Update your Linux server
* Connect to the linux server via either the Lightsail page ssh connect link or local gitbash as explained above. 
* Update server packages using the command: $ sudo apt-get update
* Upgrade the packages: $ sudo apt-get upgrade
* You can also install the user identifier package “finger” : $ sudo apt-get install finger
* Change ssh port from 22 to 2200
* Open the sshd_config file: $ sudo nano /etc/ssh/ssdh_config
* Change the ssh port from 22 to 2200
* Restart the ssh service: $ sudo service ssh restart

#### 5. Update ufw ports and status
* Allow the new port 2200: $ sudo ufw allow 2200/tcp
* Allow existing port 22: $ sudo ufw allow 80/tcp
* All UDP port 123: $ sudo ufw allow 123/udp
* Check if the ufw is active. If not, do so using the command: $ sudo ufw enable
========================================================================================================================================

### Step B: The “grader” user
#### 1. Create the grader user
* Switch role to root using the command: sudo su -
* Create the grader user: sudo adduser grader
* Assign sudo status to grader: $ sudo nano /etc/sudoers.d/grader, and type grader ALL=(ALL:ALL) ALL.


#### 2. Create a keypair for grader user
* Ssh into the grader user account: $ ssh grader@35.178.90.82 -p 2200 (plus password if any)
* Create a directory .ssh: $ sudo mkdir .ssh
* Create a file with the name authorized_keys inside the .ssh directory: $ sudo touch /.ssh/authorized_keys.
* Change the permission for the .ssh folder: $ sudo chmod 700 .ssh
* Change the permissions for the authorized_keys file: $ sudo chmod 644 /.ssh/authorized_keys
* Open a new gitbash window on your device and type the command: $ ssh-keygen
* Enter file in which to save the key (/c/Users/Hicham/.ssh/id_rsa): c/Users/Hicham/.ssh/authorized_keys
* The command will create two files in the specified directory. Open the one with the extension PUB using the command: $ sudo cat ~/.ssh/authorized_keys.pub
* Copy the content
* Open the authorized_keys file created for the grader user: $ sudo nano /.sh/authorized_keys
* Paste the content
* Reopen the sshd_config file (sudo nano /etc/ssh/sshd_config) and change password authentication from “yes” to “no”.
========================================================================================

### Step C: Apache2, mod-wsgi, and Git
#### 1. Install Apache2
* Connect to your instance with the grader account: $ ssh grader@35.178.90.82 -p 2200 -i ~/.ssh/authorized_keys
* Install apache2: $ sudo apt-get install apache2.

#### 2. Add mod-wsgi for python environment
* use the command: $ sudo apt-get install libapache2-mod-wsgi python-dev
 * Install git 
* Install git: $ sudo apt-get install git




