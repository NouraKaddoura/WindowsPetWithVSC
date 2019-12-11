## Use a Windows computer in the Cloud to get a 'Mac like' VSC Remote Connection Experience (Part 2)
### Steps

#### Generate an RSA keypair (if you don't already have one on the windows box)
```
ssh-keygen
```
#### reate your SSH Config file in the **same** folder as the private/public keys on the windows box

Here is what the SSH Config file should look like (note: the identiyFile need to match your private key):
```
Host NouraUbuntuPet
  HostName 3.135.198.243
  ForwardAgent yes
  User ubuntu
  StrictHostKeyChecking no
  IdentityFile ~/.ssh/id_rsa 
```
#### Run the following Scripts in Powershell:

```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force        # require remote signature
iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex   # setup chocolatey
choco feature enable -n allowGlobalConfirmation                 # bypass confirmations
choco install vscode -Force
code --install-extension ms-vscode-remote.remote-ssh # Add a VSC Plug in for remote connection to ubuntu machine
choco install googlechrome –Force
```

* Modify VSC Settings 
