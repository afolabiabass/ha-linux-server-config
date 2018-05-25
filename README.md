# ha-linux-server-config
A project for the requirements of Udacity FSND

#### Step A: The Lightsail instance  
##### 1. Create a Lightsail instance in AWS
* Click on the “Services” link in the top navbar
* Under the “Compute section, select Lightsail
* Inside the Lightsail page, click on “Create instance” page
* Under “Select Blueprint” section click on “OS Only”
* Select “Ubuntu”
* Select a plan. Usually the first basic plan, free for the first month then $5 afterwards
* Under “Name your instance”, rename your instance if you wish to
* Click the “Create” button. The instance will take few moments to appear on the instances page  
##### 2. Download the Lightsail default private key to local device
* In the instances page click on the instance name to open the settings page.
* Scroll all the way down to the bottom of the page and click on the blue “Account page” link
*Click on “download” at the bottom of the page, name and save the file on your local device then ssh into your Lightsail server : sudo ssh ubuntu@35.178.90.82 -i lighsail_key.pem -p 2200 )  



