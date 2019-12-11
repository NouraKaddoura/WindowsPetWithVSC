## Use a Windows computer in the Cloud to get a 'Mac like' VSC Remote Connection Experience (Part 2)


### Steps

* Generate a private/public key (if you don't already have one)

```` ssh-keygen ````

* Create your SSH Config file in the **same** folder as the private/public keys

Here is what the SSH Config file should look like (note: the identiyFile path will match your private key name):

````
Host NouraUbuntuPet

  HostName 3.135.198.243

  ForwardAgent yes

  User ubuntu

  StrictHostKeyChecking no

  IdentityFile ./.ssh/id_rsa 
  
````

* Run the following Scripts in Powershell:

````
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force

iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex

choco feature enable -n allowGlobalConfirmation

choco install terraform -Force

choco install vscode -Force

choco install git.install -Force

choco install awscli -Force

choco install sourcetree -Force

choco install googlechrome –Force

````

* Modify VSC Settings 
* Add a VSC Plug in for remote connection to ubuntu machine