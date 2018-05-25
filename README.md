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




