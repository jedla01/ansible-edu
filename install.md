
https://blog.thenets.org/how-to-run-vagrant-on-wsl-2/


## Windows features

```cmd
<!-- DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V -->
Enable-WindowsOptionalFeature -Online -FeatureName "VirtualMachinePlatform"
Enable-WindowsOptionalFeature -Online -FeatureName "Microsoft-Hyper-V"
```

## Windows packages

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
choco install git virtualbox docker-desktop
```

## WSL

[Kernel update](https://www.catalog.update.microsoft.com/Search.aspx?q=wsl)

```cmd
wsl --install
wsl -l -o
wsl --set-default-version 2
wsl --install -d Ubuntu
```

### WSL Ubuntu

Add to `/etc/wsl.conf`:
```cmd
[automount]
options = "metadata"
```

Set permissions to insecure_key:
```cmd
chmod 0700
```

## Vagrant in WSL

https://releases.hashicorp.com/vagrant/2.2.19/vagrant_2.2.19_x86_64.msi

```cmd
wget https://releases.hashicorp.com/vagrant/2.2.19/vagrant_2.2.19_x86_64.deb
sudo apt install ./vagrant_2.2.19_x86_64.deb

echo "export VAGRANT_WSL_ENABLE_WINDOWS_ACCESS=1" >> ~/.bashrc
echo 'export PATH="$PATH:/mnt/c/Program Files/Oracle/VirtualBox"' >> ~/.bashrc
echo "export VAGRANT_WSL_WINDOWS_ACCESS_USER_HOME_PATH=/mnt/c/Users/<your-personal-folder>" >> ~/.bashrc
source ~/.bashrc
```

## Vagrant WSL2 plugin

```cmd
vagrant plugin install virtualbox_WSL2
```

## Ansible

Install Ansible:
```console
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible
```
