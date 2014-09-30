How to Generate Private and Public Key
==============
$ ssh-keygen -t rsa

Change PassPhrase with changing key
==================
If you don't like you passphrase you can change it without changing the private and public key

$ ssh-keygen -p

The SSH Agent
============
$ ssh-agent $SHELL
$ ssh-add
Enter passphrase for /home/you/.ssh/id_dsa:********** <--type your passphrase
Identify added: /home/you/.ssh/id_dsa

$ git clone git@github.com:github_username/MyRepro.git

Github will not ask you for you username or password any more

