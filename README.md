Window Tiling
https://www.macupdate.com/app/mac/61314/tiles

Open in terminal Context-Menu
https://github.com/qparis/FinderOpenTerminal

Anaconda PATH on fish shell

```
export PATH="/Users/dishendra/anaconda3/bin/:$PATH"
```


### Mac Change Global View Options

Use as Defaults is supposed to carry over to all newly opened Finder windows, but it doesn't change any previously opened windows. If you want to revert all previously opened windows to that view, follow these steps:



Launch the Terminal app (in /Applications/Utilities/), copy & paste this command into the window that pops up, and hit the return key:


```shell
sudo find / -name ".DS_Store"  -exec rm {} \;
```
At the Password: prompt, carefully enter your admin password, since nothing shows up on the screen, and hit the return key. When the default prompt, usually the $ sign, pops up again, quit the Terminal app, restart, and open a Finder window, set it up the way you want, and click on Use as Defaults button. All subsequently opened or created folders should retain that view. 



### Mac OS X: Launch Terminal from keyboard shortcut

https://claudiodangelis.com/osx/2012/09/27/osx-launch-terminal-from-shortcut.html

### Proxy ON/OFF
:warning: Doesn't Works on `fish` shell use `ohmyzsh` instead.

Works if `~/.bash_profile` contains environment variables as shown below:
```shell
export http_proxy="http://<user>:<passwd>@172.16.0.1:3128/"
export https_proxy="http://<user>:<passwd>@172.16.0.1:3128/"
export ftp_proxy="http://<user>:<passwd>@172.16.0.1:3128/"

export HTTP_PROXY="http://<user>:<passwd>@172.16.0.1:3128/"
export HTTPS_PROXY="http://<user>:<passwd>@172.16.0.1:3128/"
export FTP_PROXY="http://<user>:<passwd>@172.16.0.1:3128/"

export no_proxy='localhost,127.0.0.1,*.my.lan.domain'
export NO_PROXY='localhost,127.0.0.1,*.my.lan.domain'
```

then execute commands below to add `proxy_on` and `proxy_off` functions to your shell
```shell
echo -e '\n' >> ~/.bash_profile
echo 'proxy_on(){' >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^#export[[:space:]]HTTP/export HTTP/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^#export[[:space:]]FTP/export FTP/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^#export[[:space:]]http/export http/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^#export[[:space:]]ftp/export ftp/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^#export[[:space:]]no_proxy/export no_proxy/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^#export[[:space:]]NO_PROXY/export NO_PROXY/' ~/.bash_profile " >> ~/.bash_profile
echo '}' >> ~/.bash_profile

echo -e '\n' >> ~/.bash_profile
echo 'proxy_off(){' >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^export[[:space:]]HTTP/#export HTTP/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^export[[:space:]]FTP/#export FTP/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^export[[:space:]]http/#export http/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^export[[:space:]]ftp/#export ftp/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^export[[:space:]]no_proxy/#export no_proxy/' ~/.bash_profile " >> ~/.bash_profile
echo "	sed -i -e  '/h/ s/^export[[:space:]]NO_PROXY/#export NO_PROXY/' ~/.bash_profile " >> ~/.bash_profile
echo '}' >> ~/.bash_profile
```

## Installing IDL
**Prerequesties**  
* Xquartz  
using brew: `brew cask install xquartz`  
**OR**  
using dmg from xquartz webpage: [download](https://www.xquartz.org/)  



**Installing IDL**  

Download from [here](https://drive.google.com/uc?id=1RBBZztZ3_W92uMUySzQ5RCAOYFB6uWiD&export=download)  
then `cd` to directory where you have downloaded the idl and execute following commands:  

```shell
sudo tar -xvf idl_mac.tar --directory /usr/local/
cd /usr/local/itt
sudo chmod +x /usr/local/itt/install
sudo /usr/local/itt/install
```



**Installing idl libraries**

libraries: install coyote and astron

```shell
cd ~
wget https://idlastro.gsfc.nasa.gov/ftp/coyote_astron.tar.gz
wget https://idlastro.gsfc.nasa.gov/ftp/astron.zip
mkdir astron
unzip ./astron.zip -d ./astron
tar -xvf coyote_astron.tar.gz
sudo mv ./astron/ /usr/local/itt/idl/lib/
sudo mv ./pro/coyote/ /usr/local/itt/idl/lib/
rm -rf ./pro
```

:warning:**Fixing zlib issue**

If you encounter following error:

<img src="/Users/paras/Documents/mac_setup/images/zlib_error.png" style="zoom:50%;" />

The execute following command to fix it.

```shell
sudo rm -rf /usr/local/itt/idl706/bin/bin.darwin.x86_64/libz.1.dylib
```

