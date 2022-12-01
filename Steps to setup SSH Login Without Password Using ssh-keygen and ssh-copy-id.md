# Steps to setup SSH Login Without Password Using ssh-keygen and ssh-copy-id

by [Santosh Prasad](https://www.looklinux.com/author/santosh-prasad/)

Contents...

- [Step #1: Creating Public and Private keys Using ssh-key-gen](https://www.looklinux.com/steps-to-setup-ssh-login-without-password-using-ssh-keygen-and-ssh-copy-id/#Step_1_Creating_Public_and_Private_keys_Using_ssh-key-gen "Step #1: Creating Public and Private keys Using ssh-key-gen")
- [Step #2: Copy Public Key on Remote Host using ssh-copy-id](https://www.looklinux.com/steps-to-setup-ssh-login-without-password-using-ssh-keygen-and-ssh-copy-id/#Step_2_Copy_Public_Key_on_Remote_Host_using_ssh-copy-id "Step #2: Copy Public Key on Remote Host using ssh-copy-id")
- [Step #3: Login to Remote Host without Password](https://www.looklinux.com/steps-to-setup-ssh-login-without-password-using-ssh-keygen-and-ssh-copy-id/#Step_3_Login_to_Remote_Host_without_Password "Step #3: Login to Remote Host without Password")

In this tutorial I will describe how you can setup SSH login without password using **ssh-keygen** and **ssh-copy-id.** ssh-keygen is used to create the public and private keys and ssh-copy-id used to copies the local host’s public key to the remote-host’s authorized_key file. ssh-copy-id also assigns proper permission to the remote-host’s home,  **~/.ssh**, and **~/.ssh/authorized_keys**.

Follow the below steps to login your remote Linux server without password.

## Step #1: Creating Public and Private keys Using ssh-key-gen

```bash
user@local-host$ [local-host here]
user@local-host$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa):[Press Enter key]
Enter passphrase (empty for no passphrase): [Press enter key]
Enter same passphrase again: [Press enter key]
Your identification has been saved in /home/user/.ssh/id_rsa.
Your public key has been saved in /home/user/.ssh/id_rsa.pub.
The key fingerprint is:
33:b3:fe:af:95:95:18:11:31:d5:de:96:2f:f2:35:f9 user@local-host
```




## Step #2: Copy Public Key on Remote Host using ssh-copy-id

```bash
user@local-host$ ssh-copy-id -i ~/.ssh/id_rsa.pub remote-host
user@remote-host's password:
try logging into the machine, with "ssh 'remote-host'", and check in:
.ssh/authorized_keys
Make sure we haven't added any extra keys.

Note :- ssh-copy-id will append the keys to the remote host’s .ssh/authorized_key.
```



## Step #3: Login to Remote Host without Password

```bash
user@local-host$ ssh remote-host
Last login: Mon Feb 17 17:22:33 2017 from 192.168.1.5

[Here SSH will not ask for type password.]

user@remote-host$ [Here you are on remote host]
```


