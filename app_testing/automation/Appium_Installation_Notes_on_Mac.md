# Appium Installation Notes On Mac
*Written By mengting.chen*
##**1 下载安装appium**

###1.1 通过客户端安装:

下载一个appium.dmg 双击安装即可,如果不能安装，在设置－安全与隐私－通用 里面点左下角的锁解锁，然后改为允许从任何来源下载的应用程序

[官方下载](http://appium.io/)  
[国内下载（推荐）](http://pan.baidu.com/s/1jGvAISu)

###1.2 通过命令行安装：

1.2.1 由于Appium是使用nodejs实现的，所以先装node

```shell
brew install node
```
安装完成后打开终端输入`node -v`，检查是否安装成功。
可以用appium-doctor检查是否所有dependency已经安装完


1.2.2 安装node的包管理器NPM 

```shell
git clone https://github.com/npm/npm.git
cd npm 
sudo make install
```
或者
```shell
sudo curl -L https://npmjs.org/install.sh | sh
```
安装完成后，输入`npm -v`，检查是否安装成功

1.2.3 安装Appium

```shell
npm install –g appium(千万不要加sudo)
npm --registry http://registry.npm.taobao.org install -g appium (推荐这种,npm的国内镜像)
```
**注意**：如果之前使用sudo npm install -g appium，会发现

```shell
appium
error: Appium will not work if used or installed with sudo. Please rerun/install as a non-root user. If you had to install Appium using `sudo npm install -g appium`, the solution is to reinstall Node using a method (Homebrew, for example) that doesn't require sudo to install global npm packages.
```
此时只能重装node 、 appium

```shell
brew uninstall node
brew install node
sudo chown -R mengting ~/.npm
sudo chown -R mengting /usr/local/lib/node_modules
npm install –g appium
```

##2 下载对应语言需要的appium-client
```shell
sudo pip install Appium-Python-Client
```
##3 对模拟器的要求
* 1.3.3的appium最多只支持iOS7.1的simulator，xcode 6 默认都是iOS8的simulator，所以需要额外去下载模拟器  
X-Code->Prefrences-> Downloads componants  
里面可以下载iOS7.1 simulator

* appium跑4.2之前的android模拟器跑不起来  
>Android devices before version 4.2 (API Level 17) do not have Google's UiAutomator framework installed. This is what Appium uses to perform the automation behaviors on the device. 

##4 模拟器的键盘
* 如果case里面要用到键盘，xcode6里面需要把模拟器对应的软键盘调出来

>If you’re on Xcode 6, you need to launch each simulator you intend to use with appium in advance, and change the default to actually show the soft keyboard if you want sendKeys to work. You can do this by clicking on any textfield and hitting command-K until you notice the soft keyboard show up.

##参考资料
1.官方网站<http://appium.io>  
2.博客<http://www.cnblogs.com/tangdongchu/tag/appium/>   
3.stackoverflow上的问题解答<http://stackoverflow.com/questions/18923191/npm-install-fails>