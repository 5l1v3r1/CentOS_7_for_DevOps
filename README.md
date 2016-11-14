
##I use most Google Apps like Drive, Docs, Gmail...


# MENU
- [Install epel and nux repo?](###Install-epel-and-nux-repositories-)


###1 - Install epel and nux repositories

```
sudo yum -y install epel-release && sudo rpm -Uvh http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm
```
###1.1 Update the whole system

```
sudo yum -y update
```

2 - Install Google Chrome
 
 Create the repo file in /etc/yum.repos.d/google-chrome.repo

```
sudo tee /etc/yum.repos.d/google-chrome.repo <<-'EOF'
[google-chrome]
name=google-chrome
baseurl=http://dl.google.com/linux/chrome/rpm/stable/$basearch
enabled=1
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub
EOF
``` 

Installing...

```sh
sudo yum -y install google-chrome-stable
```

3 - Install Other Packages(apps)

```
sudo yum -y install skype gvim vlc vlc-core git zsh stow filezilla transmission unrar
```

4 - Install oh-my-zsh

```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

5 - Remove packages (I remove packages that I dont use)

```
sudo yum -y remove firefox evolution rhythmbox totem gedit ekiga empathy libreoffice-core
```

6 - Install latest Docker, using docker repo.

```
sudo tee /etc/yum.repos.d/docker.repo <<-'EOF'
[dockerrepo]
name=Docker Repository
baseurl=https://yum.dockerproject.org/repo/main/centos/7/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
EOF
```

```
sudo yum install docker-engine
```

```
sudo systemctl enable docker
sudo systemctl start docker
```

7 - Install Virtualbox

```
sudo curl -o /etc/yum.repos.d/virtualbox.repo http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo
```

```
sudo yum -y install dkms kernel-headers kernel-devel fontforge binutils glibc-headers glibc-devel
sudo yum -y install VirtualBox-5.1
```

```
sudo su
export KERN_DIR=/usr/src/kernels/3.10.0-327.36.3.el7.x86_64
/usr/lib/virtualbox/vboxdrv.sh setup
```

Add your user into vboxusers

```
sudo usermod -a -G vboxusers username
```

8 - Installing Vagrant.

```
sudo rpm -ivh https://releases.hashicorp.com/vagrant/1.8.7/vagrant_1.8.7_x86_64.rpm
```

9 - Change the icons to numix-icon-theme-circle

```
mkdir /home/USER/.icons
cd /tmp
git clone https://github.com/numixproject/numix-icon-theme-circle.git
cd /tmp/numix-icon-theme-circle
mv * /home/USER/.icons
```

Now open Tweak Tool -> Appearance -> Icons -> Numix-Circle


10 - Fix the keyboard for Thinkpad T420

```
setxkbmap -model thinkpad60 -layout br
```
