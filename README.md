How to Generate Private and Public Key
=======================================
$ ssh-keygen -t rsa       <-- this tell ssh to generate a key rsa type key. 

Generating public/private rsa key pair.
Enter file in which to save the key (/c/users/username/.ssh/id_rsa): <--don't add anything here.

/c/users/username/.ssh/id_rsa already exists.

Overwrite (y/n) y  <--- type y if you want to delete the old key.

Enter passphrase (empty for no passphrase):xxxxxxxxxxxxxxxxxx


Enter same passphrase again:xxxxxxxxxxxxxxxxx
Your identification has been saved in id_rsa.

Your public Key has been saved in id_rsa.pub.

The key finger print is:
f3:15:57:.....................:db username@domain.com  <---- note this is not a key but finger print. You should try to remember its appearance or image.

Two keys will be generated. The private key you keep on you main computer and the public key (with the .pub extension) you store it at the remote host (raspberry pi). The private key should always be stored on your main computer.

How to change the passphrase.
==============================
If you made a mistake and don't like your old passphrase you can change it without changing the private and public keys. Type the following command:

$ ssh-keygen -p  <--- by add -p you're requesting to change the passphrase. Don't worry this doesn't change the key.

Start the SSH Agent
===================
$ ssh-agent $SHELL
$ ssh-add
Enter passphrase for /home/you/.ssh/id_rsa:xxxxxxxxxxxxxx     <--type your passphrase here.
Identify added: /home/you/.ssh/id_rsa

Setup the Raspberry Pi
==================
Copy your public key to your ~/.ssh folder. In the .ssh folder you should see a file named authorized_keys. If you don't see it, type the following command

$ touch authorized_keys   <--- this just creates a blank file with nothing inside.

Next use the following command to append the public key to your authorized_keys file on the Pi, sending it over SSH:

cat ~/.ssh/id_rsa.pub | ssh <USERNAME>@<IP-ADDRESS> 'cat >> .ssh/authorized_keys'

If you typed everything correct, next time log on with ssh-agent you will not have to authenticate with your password.

Transfering files without username or password

$ git clone git@github.com:github_username/MyRepro.git

By this point, Github shouldn't not be asking you for your username or password any more. If GitHub does, you probability made a mistake somewhere in the setup.

