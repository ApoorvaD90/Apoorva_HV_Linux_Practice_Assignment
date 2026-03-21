# Apoorva_HV_Linux_Practice_Assignment
This repo is for Linux practice assignment

All the steps with screenshots are also added to a word document added to the Git repo

Task 1:
1. htop is installed using 'sudo apt install htop' command
2. The processes are returned using 'htop' command after installation
3. 'df' and 'du' commands return the disk usage

Task 2:
1. Create user sarah using command 'sudo adduser sarah'
2. Create workspace folder within sarah
3. Create user mike using command 'sudo adduser mike'
4. Create workspave folder within mike
5. ls -ltr can be used to view the permissions on sarah and mike folders
6. chmod command can be used to modify these permissions if required
7. For respective users to be only allowed access to their folders the access should be rwx-----. This will give access to only user to access to their own folder
7. password policy can be applied for 30 days using command 'sudo chage -M 30 sarah' and similar for mike

Task 3:
1. Apache is installed using command 'sudo apt install apache2'
2. tar file can be created for apache folder using command 'sudo tar -czvf apache2_backup_2026_03_22.tar.gz apache2 in the /etc folder
3. tar file can be created for /var/www/html using command 'sudo tar -czvf index_2026_03_22.tar.gz index.html in the /var/www/html folder
4. tar file can be created for nginx folder using command 'sudo tar -czvf nginx_backup_2026_03_22.tar.gz nginx in the /etc folder
5. tar file can be created for /usr/share/nginx/html/ using command 'sudo tar -czvf index_2026_03_22.tar.gz index.html in the /usr/share/nginx/html/ folder
6. cron job can be created within the crontab to run the backups every tuesday 12 AM '0 0 * * 2 apache_backup.sh'. This will run the backup script for apache. The backup script is creating backup file for apache and /var/www/html folder. The backup script conatins below lines:

#!/bin/bash

BACKUP_FOL="backups"
DATE=$(date +%F)

mkdir -p $BACKUP_FOL

sudo tar -czf $BACKUP_FOL/apache_backup_$DATE.tar.gz /etc/apache2
sudo tar -czf $BACKUP_FOL/index_backup_$DATE.tax.gz /var/www/html
7. Similarly, cron job can be created within the crontab to run the backups every tuesday 12 AM '0 0 * * 2 nginx_backup.sh'. This will run the backup script for nginx. The backup script is creating backup file for apache and /var/www/html folder. The backup script conatins below lines: 

#!/bin/bash

BACKUP_FOL="backups"
DATE=$(date +%F)

mkdir -p $BACKUP_FOL

sudo tar -czf $BACKUP_FOL/nginx_backup_$DATE.tar.gz /etc/nginx
sudo tar -czf $BACKUP_FOL/index_nginx_backup_$DATE.tax.gz /usr/share/nginx/html