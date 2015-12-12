#CentOS 7 Linux SDC 编译环境
##0. 安装Qt 32位和64位编译库
	# yum install qt-devel.i686 qt-devel.x86_64
##1. 安装缺失编译库
	# yum install glibc-devel.i686
##2. 安装libUSB编译库
	# yum install libusb-devel.i686 libusb-devel.x86_64
##3. 生成MakeFile文件
生成32位MakeFile文件
	$ qmake-qt4 -makefile -spec linux-g++-32 -o Makefile
生成64位MakeFile文件
	$ qmake-qt4 -makefile -o Makefile
