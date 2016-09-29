How to Generate Private and Public Key
=======================================

> <code>$ ssh-keygen -t rsa</code>

This command tell ssh to generate a rsa type key. The following message will display:

<code>Generating public/private rsa key pair.</code>

<code>Enter file in which to save the key (/c/users/username/.ssh/id_rsa): </code>

If the file path is correct, do not type any informatin just press Enter. The following message will appear:

> <code>/c/users/username/.ssh/id_rsa already exists.</code>

> <code>Overwrite (y/n)</code>

If you want to delete the old key, type <code>y</code> and press <code>Enter</code>. Otherwise type <code>n</code>. The following message will appear:

> <code>Enter passphrase (empty for no passphrase):</code>

Type a passphrase you can remember (not too complicated) and press <code>Enter</code>. The following message will appear:

> <code>Enter same passphrase again:</code>

Retype the passphrase again and press <code>Enter<code>. The following message will appear:

> <code>Your identification has been saved in id_rsa.</code>

> <code>Your public Key has been saved in id_rsa.pub.</code>

> <code>The key finger print is:</code>

> <code>f3:15:57:.....................:db username@domain.com </code>

Try to remember the finger print image (appearance). You don't need to memorize the actual message.
Note, two keys will be generated, a public key and a private key. The private key should be stored on your main computer and the public key (with the .pub extension) should be stored at the remote host (example. raspberry pi, github,...,etc). 

How to change the passphrase.
==============================
If you made a mistake or don't like your old passphrase, you can change it without changing the private and public keys. Type the following command:

> <code>$ ssh-keygen -p </code>  

The <code>-p</code> is requesting to change the passphrase only. Don't worry this doesn't change the key.


Start the SSH Agent
===================

The the following commands:

> <code>$ ssh-agent $SHELL</code>

> <code>$ ssh-add</code>

The following message will appear:

> <code>Enter passphrase for /home/you/.ssh/id_rsa:</code>

> <code>Identify added: /home/you/.ssh/id_rsa</code>

Setup the Raspberry Pi
==================
Copy your public ssh key to your <code> ~/.ssh</code> folder. In the .ssh folder, you should see a text file named <code>authorized_keys</code>. If you don't see it, type the following command

> <code>$ touch authorized_keys</code>

<code>touch</code> is a Linux command that creates a blank text file with nothing inside.

Next type the following command to append the public key to your authorized_keys file on the Pi, sending it over SSH:

> <code>$ cat ~/.ssh/id_rsa.pub | ssh <USERNAME>@<IP-ADDRESS> 'cat >> .ssh/authorized_keys'</code>

If you typed everything correctly, next time you run the ssh-agent you will not have to authenticate with your password.

Transfering files without username or password
==============================================

> <code>$ git clone git@github.com:github_username/MyRepro.git</code>

By this point, Github shouldn't not be asking you for your username or password any more. If GitHub does, you probability made a mistake somewhere in the setup.

