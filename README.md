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
   
   在初步安装完成后，选择Custom安装项：
   ![image](https://github.com/mingmingYu1/first-react-native-App-step/blob/master/images/react-native-android-sdk-environment-variable-windows.png)
