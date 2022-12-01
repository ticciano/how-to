# How To Setup Automatic Remote Backup With Rsync

by [Santosh Prasad](https://www.looklinux.com/author/santosh-prasad/)

Backup is most important task for any server administrator these days, all Linux users know about rsync as a file transfer utility, but using rsync we can also automate remote backups of our Linux, Windows, and Mac OS X system.

In this article I will explain how to setup automatic backups with rsync.

To perform automatic secure remote backup, make sure you have rsync and SSH installed on both your local system and your remote system. Follow the below link to install Rsync and SSH on the system.

**Suggested Read : [Install Rsync And SSH On The Linux System](https://www.looklinux.com/how-to-setup-remote-backup-with-rsync/)**

## Automatic Backups

First step to automatic remote backups is to remove any required user intervention namely requests for SSH password. To access your systems without asking for a password, you will need to generate passphrase-less keys on the local machine and copy the public key into the remote machine user’s home directory.

Follow the below link to setup SSH login without password:

**Suggested Read : [Steps To Setup SSH Login Without Password](https://www.looklinux.com/steps-to-setup-ssh-login-without%20password-using-ssh-keygen-and-ssh-copy-id/)**

Now you should be able to SSH into the remote machine without password.

`ssh -i /home/user/.ssh/id_rsa user@remotehost.com`

Rsync should now complete without prompting for a password. Lets take a backup.

`rsync -avz -e "ssh -i /home/user/.ssh/id_rsa" /root/test/ remote_user@remotehost.com:/backup/destination/directory/`

Still if your are getting problem, please make sure you have set proper permission to read from the source “**/root/test/**” and to write to the target “**remote_user@remotehost.com:/backup/destination/directory/**” also make sure ssh session is establishing between the two hosts without password.

## Set Cron Job For Automatic  Backup

Now set cron jop for automate this process on scheduled time.

# crontab -e

`30 2 * * * rsync -avz -e "ssh -i /home/user/.ssh/id_rsa" /root/test/ remote_user@remotehost.com:/backup/destination/directory/`

After you are done configuring Cron, press escape, and then type “:wq” (without the quotes) and press enter. This will save your changes in vi.

In the above cron it is scheduled to perform automatic backup on daily at 2:30 PM. Most people will just want a simple weekly or daily backup, and what we have shown you can easily accomplish that. For more info about Cron, please see my previous article.

[Source - www.looklinux.com](https://www.looklinux.com/how-to-setup-automatic-remote-backup-with-rsync/)
