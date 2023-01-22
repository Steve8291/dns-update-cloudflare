# dns-update-cloudflare
Bash script to update a dynamic dns to CloudFlare.  
Script will email on errors and successful updates of DNS.  
Also performs a monthly force update of your DNS Records even if your ip address hasn't changed.  
An email is sent after a force update in order to let you know that everything is still operational.  

## Requirements:
Tested on Ubuntu 20.04 Focal Fossa and 22.04 Jammy Jellyfish.  
Script assumes you have a working mail server (postfix, etc) so that it can send you updates.  
You will also need to install curl and jq.  
example: `sudo apt install curl jq`  

## Usage:
1. Save the script someplace like /home/username/scripts/dns-update.sh  
2. Change permissions to make it executable: `sudo chmod 700 /home/username/scripts/dns-update.sh`  
3. Open the script file and configure the Settings at the top of the file.  
4. You will need to know your email address, zone id from CloudFlare, api token from CloudFlare, and domain names.  
5. Either place the script directly into one of the cron dirs, symlink it there, or put a line to execute it directlty into crontab.  
* If you place the script directly into cron.hourly make sure to leave off the extension `.sh`  
* Symlink to cron.hourly: `ln -s /home/username/scripts/dns-update.sh /etc/cron.hourly/dns-update`  
* Add to crontab: `crontab -e` and add line `0 * * * * /home/username/scripts/dns-update.sh` to have it run hourly on the hour.  
