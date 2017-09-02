
## CentOS 7 Desktop for DevOps Engineer

1. [Install Repositories](#1---install-epel-and-nux-repositories)
2. [Install Google Chrome](#2---install-google-chrome)


### 1 - Install epel and nux repositories

```
sudo yum -y install epel-release && sudo rpm -Uvh http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm
```
### 1.1 Update the whole system

```
sudo yum -y update
```

### 2 - Install Google Chrome

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

### 3 - Install Other Packages(apps)

```
sudo yum -y install skype gvim vlc vlc-core git zsh stow filezilla transmission unrar
```

### 4 - Install oh-my-zsh

```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### 5 - Remove packages (I remove packages that I don't use)

```
sudo yum -y remove firefox evolution rhythmbox totem gedit ekiga empathy libreoffice-core
```

### 6 - Install latest Docker, using docker repo.

```
sudo yum-config-manager \
     --add-repo \
     https://download.docker.com/linux/centos/docker-ce.repo

```
sudo yum install docker-ce
```

```
sudo systemctl enable docker
sudo systemctl start docker
```

### 7 - Installing docker-compose

```
sudo yum install -y python-pip
pip install docker-compose
```

### 8 - Install Virtualbox

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

### 9 - Installing Vagrant.

```
sudo rpm -ivh https://releases.hashicorp.com/vagrant/1.9.2/vagrant_1.9.2_x86_64.rpm
```

### 10 - Change the icons to numix-icon-theme-circle

```
mkdir /home/USER/.icons
cd /tmp
git clone https://github.com/numixproject/numix-icon-theme-circle.git
cd /tmp/numix-icon-theme-circle
mv * /home/USER/.icons
```

Now open Tweak Tool -> Appearance -> Icons -> Numix-Circle


### 11 - Fix the keyboard for Thinkpad T420

```
setxkbmap -model thinkpad60 -layout br
```

### 12 - Install latest versoin of git


I use the different path for programs that I compile local in my machine.

**/home/USER/Programs/PROGRAM_NAME/VERSION**

and later I export the PATH.

```
wget https://github.com/git/git/archive/v2.11.1.zip
cd git-2.11.1

make configure
./configure --prefix=/home/ricardson/Programs/git/2.11.1/ --with-curl

make install
```

Need to add the path indo .zshrc like below:

```
$HOME/Programs/git/2.11.1/bin
```

**You can also check my [.zshrc](https://github.com/ricardson/dotfiles/blob/master/zshrc/.zshrc) file.**


