1、下载chocolatey软件，用于安装windows上的系统软件，如node，git等 

  命令： 
    @powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object ne   t.webclient).DownloadString
    ('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
	 
2、下载Python2,  注意目前不支持Python 3版本

  命令： choco install python2 （用chocolatey下载）

3、下载node

   命令： choco install nodejs.install  （用chocolatey下载）
   
   将npm设置国内镜像，加速npm的下载
   
   npm config set registry https://registry.npm.taobao.org --global
   
   npm config set disturl https://npm.taobao.org/dist --global
   
4、下载React-native命令行工具（react-native-cli）

   命令：npm install -g react-native-cli
   
5、安装Android Studio编辑器  React Native目前需要Android Studio2.0或更高版本。

   Android Studio需要Java Development Kit [JDK] 1.8或更高版本。你可以在命令中输入 javac -version来查看你当前安装的JDK版本。
   如果版本不合要求，则可以到 官网上下载。 或是使用包管理器来安装（比如choco install jdk8或是 apt-get install default-jdk）
   
   Android Studio包含了运行和测试React Native应用所需的Android SDK和模拟器。
   
   除非特别注明，请不要改动安装过程中的选项。比如Android Studio默认安装了 Android Support Repository，而这也是React Native必须的
   否则在react-native run-android时会报appcompat-v7包找不到的错误。
   
   确定所有安装都勾选了，尤其是Android SDK和Android Device Emulator。
   
   在初步安装完成后，选择Custom安装项：

   ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/react-native-android-studio-custom-install-windows.png)
   
   检查已安装的组件，尤其是模拟器和HAXM加速驱动。

   ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/react-native-android-studio-verify-installs-windows.png)
   
   安装完成后，在Android Studio的欢迎界面中选择Configure | SDK Manager。

   ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/react-native-android-studio-configure-sdk-windows.png)
   
   在SDK Platforms窗口中，选择Show Package Details，然后在Android 6.0 (Marshmallow)中勾选Google APIs、Intel x86 Atom System Image、Intel x86   Atom_64 System Image以及Google APIs Intel x86 Atom_64 System Image

   ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/react-native-android-studio-android-sdk-platforms-windows.png)

   在SDK Tools窗口中，选择Show Package Details，然后在Android SDK Build Tools中勾选Android SDK Build-Tools 23.0.1。（必须是这个版本）

   ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/imagesreact-native-android-studio-android-sdk-build-tools-windows.png)

6、ANDROID_HOME环境变量

  确保ANDROID_HOME环境变量正确地指向了你安装的Android SDK的路径。
  打开控制面板 -> 系统和安全 -> 系统 -> 高级系统设置 -> 高级 -> 环境变量 -> 新建

  ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/react-native-android-sdk-environment-variable-windows.png)

7、将Android SDK的Tools目录添加到PATH变量中

  你可以把Android SDK的tools和platform-tools目录添加到PATH变量中，以便在终端中运行一些Android工具，例如android avd或是adb logcat等

  打开控制面板 -> 系统和安全 -> 系统 -> 高级系统设置 -> 高级 -> 环境变量 -> 选中PATH -> 双击进行编辑

  ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/react-native-android-tools-environment-variable-windows.png)

8、安装git

  命令： choco install git
  
  另外你也可以直接去下载Git for Windows。 在安装过程中注意勾选"Run Git from Windows Command Prompt"，这样才会把git命令添加到PATH环境变量中
  
9、安装Genymotion（安卓虚拟机,比起Android Studio自带的原装模拟器，Genymotion是一个性能更好的选择，但它只对个人用户免费）
  
  下载和安装Genymotion（译注：不要被里面的价格唬住了，个人免费的链接可能不明显，请仔细寻找！另外，genymotion需要依赖VirtualBox虚拟机，下载选项中提   供了包含VirtualBox和不包含的选项，请按需选择）。
  
  打开Genymotion。如果你还没有安装VirtualBox，则此时会提示你安装。
  
  创建一个新模拟器。
  
  ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/Genymotion.png)
  
  点击start

  ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/GenymotionShell.png)
  
10、下载react-native项目

    react-native init AwesomeProject

11、有个常见的问题是在你运行react-native

    run-android命令后，Packger可能不会自动运行。此时你可以手动启动它

    cd AwesomeProject
    react-native start
    
    访问：http://localhost:8081/index.android.bundle?platform=android
    连接成功如图
    ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/platform=android.png)
    
    如果你碰到了ERROR Watcher took too long to load的报错，请尝试将这个文件中的MAX_WAIT_TIME值改得更大一些 (文件在node_modules/react-native/目     录下)。
 
 13、Android平台运行（联机测试）

   a、Android模拟器，使用的是genymotion
   
     查看当前的设备列表信息命令：adb devices
     
     ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/adbDevices1.png)
   
   b、Android真机测试
      如果你需要应用运行在真机设备中，那么我们首先设备要开启USB调试模式
      
      真机打开USB调试模式之后，然后连接电脑，再次命令行adb 

      devices可以查看当前的设备列表信息，如下图所示： 

      ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/adbDevices2.png)
      
   现在大家可以看到里边有一台设备已经连接了，不过如果我们需要运行应用的话，那我们必须确保当前只有一台设备连接否则会报错，光是连接了设备并没有完成步      骤，还是要让设备和电脑在同一个WiFi环境下面。
   
  14、运行react-native run-android
     
     接着就开始编译代码了，然后运行程序到设备中了。其实这时，你会发现会发生屏幕是红色的。截图如下：

     ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/startEror.png)
     
     解决步骤如下：
     
     Android 5.0以上及更高版本通过以下方式： 
     
       使用adb reverse命令 
     
       首先你的设备连接电脑，然后打开USB调试模式。接着命令行运行 
     
       adb reverse tcp:8081 tcp:8081 
     
       然后我们就可以使用Reload JS和其他的开发选项了（目前没有测试）
     
     Android5.0以下版本解决方式：
     
       a. 摇晃设备或者命令行输入adb shell input keyevent 82，打开开发者菜单，如下效果： 

          ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/ReloadJs.png)
	
        b. 点击Dev Setting进入，然后选择Debug server host & port for device 
     
       c. 输入电脑的IP地址和端口号（主要查看电脑的IP地址，这边用我的IP地址和端口，具体根据实际情况哦），截图如下： 

          ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/zhengjiIp.png)
	
       d. 回到开发者菜单，然后选择点击Reload JS.重新加载即可
     
     虚拟机调试解决方法  

       app启动之后会提示无法连接到服务器，需要在app上设置服务器的ip和port 

       ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/2301838-74dd0b6a0750f44c.png)

       ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/2301838-3113a031fbdae797.png)

       ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/2301838-bbaaf68948d8722a.png)

       ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/2301838-7c565d70be087c9d.png)
       
       双击RR键刷新
     
     
 
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
